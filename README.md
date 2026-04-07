# mermaid
<pre>mermaid
graph TD
    subgraph Team [فريق العمل - 7 مطورين]
        DevOps[مطور DevOps - 1]
        Node[مطوري Node.js - 2]
        React[مطور React.js - 1]
        Flutter[مطوري Flutter - 3]
    end

    subgraph Products [الحسابات الأربعة - تطوير متوازي]
        Admin[المدير/الإداري - لوحة الويب]
        Teacher[المعلمة - تطبيق الموبايل]
        Student[الطالب - تطبيق الموبايل]
        Parent[ولي الأمر - تطبيق الموبايل]
    end

    subgraph GitHub_Workflow [سير العمل في GitHub Projects]
        Backlog(Product Backlog<br>المهام الكلية)
        Sprint(Sprint Backlog<br>مهام الأسبوع)
        InProgress(In Progress<br>قيد التنفيذ)
        Review(Code Review/QA<br>المراجعة والاختبار)
        Done(Done<br>مكتمل)
    end

    DevOps -.->|تجهيز السيرفرات وقواعد البيانات| Node
    Node -.->|بناء الـ APIs| Products
    React ===>|تطوير الواجهات| Admin
    Flutter ===>|تطوير الواجهات| Teacher & Student & Parent

    Products --> Backlog
    Backlog --> Sprint
    Sprint --> InProgress
    InProgress --> Review
    Review --> Done
<pre/>
