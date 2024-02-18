+++ 
date = 2021-07-30T17:17:36+02:00
title = "ماذا لو: مزنوق في الوقت ولازم أغير جزء ما؟"
description = ""
slug = ""
tags = ["tdd", "unit-testing", "legacy-code"]
categories = ["software-engineering", "clean-code"]
externalLink = ""
series = ["working effectively with legacy code"]
+++
# ماذا لو: مزنوق في الوقت ولازم أغير جزء ما؟


### الفصل ٦. ماذا يفعل السيد المبرمج لما يكون مزنوق في الوقت ومضطر يعمل تغيير ما في كود قديم؟

- بداية: رغم أن الوقت اللي ممكن تعمل فيه التغيير بدون إضافة tests حواليه **قد يبدو** أقل (بدون الـ tests حوالي ١٥ د في مقابل ساعتين لو عملت حبة refactors وضيفت الـ tests على سبيل المثال) بس دي نظرة قاصرة، لأنك محسبتش الوقت اللي كنت ممكن تأخده في الـ debugging والـ patching لو كنت تجاهلت الـ tests. ده بعيدًا عن تكلفة الصيانة على المدي البعيد.
- ملاحظة سريعة: تغييرات الـ systems في الأغلب بتميل أنها تبقي في نفس الأماكن في المدى الزمني القريب، بما يعني أن اللي غيرته النهاردة في الأغلب هتعدل عليه قريبًا، فده استثمار مهم حتى على المدي القريب، حتى لو مكنتش مدرك ده في لحظتها.
- الكتاب ف الفصل السادس بيناقش شوية طرق تقدر تعدل بيها الكود اللي موجود، اللي مالوش test coverage، بشكل يسمحلك تضيف tests لتغييراتك بشكل مبدئى، عشان يبقي عندك قدر من الثقة في تعديلاتك وما قد ينتج عنها من آثار جانبية side effects.


---

## Sprout Method:

### What:

لما يكون تكون الـ new requirements بتاعتك ممكن تتكتب كاملة بشكل منفصل عن الكود اللي موجود بالفعل، فتكتبها في new methods، الـ new methods دي اسمها sprout methods. كأنها براعم جديدة بتنبت في شجرة الـ code بتاعتك. بعد ما تكتب الـ new sprouted methods دي، ناديها من الأماكن اللي محتاجها في الـ code base بتاعتك. ده بعد ما تكتب لل sprouted methods دي test cases طبعًا.

### When:

- لما يكون الـ new code to be added منفصل بشكل واضح عن الـ existing code، وغير معتمد عليه بشكل مباشر.
- لما تكون مش عارف تكتب tests للـ method الرئيسية اللي بتستخدم الـ sprouted method منها.

### How:

1. حدد مكان التغيرات المطلوبة.
2. اكتب الـ new method call حتى لو لسه مكتبتش الـ method نفسها، وبعدين comment it.
3. حدد إيه الـ arguments اللي الـ new sprouted method محتاجاها، وباصيها للـ new call.
4. حدد إيه الـ return من الـ newly sprouted method، وعرّف new var and assign the return to it.
5. اكتب الـ sprouted method، باستخدام TDD. (اكتب لها الـ tests الأول، وبعدين اكتب الـ method بحيث أنها تعدي الـ tests اللي اتكتبت)
6. شيل الـ comment من علي الـ newly sprouted method من الـ call site اللي كنت كتبتها فيه.

### Pros:

- Testability for newly added code.
- Clear separation between old code and new code, which allows nice in case you needed to reuse the new code else where in the same class.

### Cons:

- When you're creating a sprout method, you're giving up on getting exiting class/method under tests. This can be a practical choice sometimes, but it's still a sad fact. Please get back to the design boards and try to refactor the main peace of code that was causing the need for the sprout in the first place.

---

## Sprout Class:

### What:

هي نفس فكرة الـ sprout method، مع الفارق أنك أحيانًا مش هتعرف تكتب tests للـ sprout methods الجديدة اللي كتبتها عشان مش عارف تـ create an instance of this class into test harness لأي سبب: مثلًا في creational dependencies كتيرة للـ class دي، أو فيها hidden dependencies كتير مثلًا. في الحالات المماثلة ممكن تعمل a totally new class وتضيف فيها الـ new requirements بتاعتك، وتبقي دي الـ sprouted class بتاعتك اللي هتكتبلها tests.

### When:

- You're adding a totally new responsibility to some existing class.
- You're adding small changes to an existing class that can't be part of test harness yet. (Otherwise you can add your changes as *sprout method* instead)

### How:

1. حدد مكان التغيرات المطلوبة.
2. اختار اسم ملائم للـ new class بتاعتك، واعمل منها new instance في مكان التغييرات المطلوبة، ونادي علي method جواها - لسه هتكتبها - عشان تعمل الـ processing المطلوب
3. حدد إيه الـ arguments اللي الـ new class محتاجاها، وباصيها للـ constructor أو للـ method.
4. حدد إيه الـ return من الـ newly sprouted class، وعرّف new var and assign the return to it.
5. اكتب الـ sprouted class، باستخدام TDD. (اكتب لها الـ tests الأول، وبعدين اكتب الـ class بحيث أنها تعدي الـ tests اللي اتكتبت)
6. شيل الـ comment من علي الـ newly sprouted class method call من الـ call site اللي كنت كتبتها فيه.

### Pros:

- ثقة أكتر في التغييرات وصوابها، بما أنها متغطية بـ tests.

### Cons:

- ممكن تبقي بتضيف تعقيد أكتر للـ code base بتاعتك، بما أنها new class فده يعني more build time وكمان more effort to understand the bussines. ده ممكن يكون منطقي في حالة أن الـ newly added class بتضيف مفهوم جديد منطقي للـ code base مثلًا، أو ببساطة لأنك معندكش حل بديل عشان تضيف tests للتغيرات بتاعتك.

---

## Wrap method:

### What:

لما تلاقي أنك عايز تضيف requirements جديدة مرتبطة بحاجة معمولة بالفعل، بس في نفس الوقت مش عايزهم يكون مرتبطين أكتر من اللازم tightly coupled. بتعمل method جديدة بنفس اسم القديمة، وتغير اسم القديمة، وتنادي من الجديدة علي القديمة. كأنك لفيت/wrapped الـ existing functionality بـ new functionality. كمثال سريع ومبسّط: إضافة logs لـ existing functionality.

### When:

- لما تكون الـ new functionality منفصلة بشكل واضح وصريح ولا تعتمد علي أي حاجة من الـ existing code.

### How: *If we need to keep the old functionality reachable as well*

1. حدد مكان الـ method اللي محتاج تغيرها.
2. غير اسم الـ method القديمة لاسم مختلف، بعدين اعمل method جديدة بنفس بصمة الـ method القديمة.
3. نادي على الـ method اللي أنت غيرت اسمها داخل الـ method اللي أنت لسه عاملها بنفس الاسم.
4. اعمل new method فيها الـ newly required changes، ومتنساش تكتبلها tests الأول كالمعتاد.
5. نادي على الـ new method that you created in 4 جوه الـ method اللي أنت عملتها في step 2.

### How: *If we don't need to keep the old functionality reachable by itself*

1. حدد مكان التغييرات المطلوبة.
2. اعمل الـ method الجديدة اللي بتعمل الـ newly added requirements، واكتبلها its own tests.
3. create a new method that calls both the old existing method and the method created in step 2.

### Example:

- Read the book. (pg 67-70) لأنها بتلخط فعلًا.

### Pros:

- فصل واضح بين الـ newly added code والـ already existing code.

### Cons:

- Can lead to poor naming sometimes.

---

## Warp Class:

### What:

- ببساطة، هي الـ class lvl companion to wrap method.
- a.k.a: Decorator pattern in same cases.

### When:

- You're adding small changes to an existing class that can't be part of test harness yet. (Otherwise you can add your changes as *wrap method* instead)

### How:

1. حدد مكان الـ method اللي محتاجة تعديل.
2. أعمل class جديدة وابعتلها الـ class اللي عايز تلفها/wrap it في الـ constructor بتاعها.
3. أعمل new method في الـ class الجديدة بتعمل الـ new requirements، ومتنساش تكتب لها tests الأول.
4. من جواه الـ new method in the new class، نادي على existing method في الـ class القديمة اللي باصيتها في الـ constructor.
5. أعمل instance من الـ wrapper class الجديدة في المكان اللي محتاجه فيها، ونادي علي الـ new method.

📌 **SUMMARY: You can use the Sprout and/or Wrap methods for classes and/or methods to better add code to classes that's can't be tested easily. That's until you can get them into a test harness.**

---

## Sprout vs Wrapper methods: Final thoughts

- في واقع الأمر، الفارق بينهم طفيف جدًا، السيد مايكل سي. فيثارس يرجحهم بناءًا على التالي:
    - في حالة ما إذا كان الكود الموجود بالفعل بيوصل خوارزمية algorithm واضحة وقائمة بذاتها لمن يقرأ الكود ← في الأغلب بيروح للـ Sprout method، بما يعني إضافة الجديد واستخدامه كجزء من الخوارزمية الموجودة بالفعل.
    - في حالة ما إذا كان الكود المضاف يماثل في أهميته الكود الموجود بالفعل ← في الأغلب بيروح للـ wrapper method، بما يعني وكأنه خلق خوازمية جديدة تتكون من الكود القديم وبعده/قبله الإضافة الجديدة.
    - بينما عشان نروح للـ Wrapper class، محتاجين requirements نسبيًا يمكن تلخيصها في التالي:
        - الإضافات المطلوبة مستقلة تمامًا بذاتها، ومش حابب يلوث اللي موجود بالفعل بإضافة responsibilities جديدة ليها مش بالضرورة جزء منها..
        - الـ class الأساسية حجمها زاد جدًا لدرجة أنه مش حابب يزود الطين بلة، فبيفضل يـ wrap it وكأنه بيـ draw a new line عشان التغييرات اللي جاية تتضاف علي ال class الجديدة بدل القديمة.
    
    ---
    

> أهم مشاكل التطوير في الأنظمة العتيقة، هي - ببساطة - الكود الموجود بالفعل.. مش لصعوبة فهمه أو تغييره فقط، ولكن ببساطة لأنه بيخلينا نتصور أنه مستحيل التغيير، وأنه مهما عملنا فيه هيفضل سيء كما هو..
>بس على المدى المتوسط والبعيد، التغييرات الطفيفة المستمرة قادرة على إحداث اختلافات جذرية جيدة في الأنظمة العتيقة..
>أحيانًا إلى الدرجة اللي ممكن تفتح نفسك على الشغل تاني من أول وجديد. : )))

- السيد مايكل سي. فيثارس، بتصرف.
>