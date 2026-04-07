```mermaid
flowchart TB
    %% تعريف الألوان والاستايلات
    classDef planning fill:#f9f871,stroke:#333,stroke-width:2px,color:#333
    classDef backend fill:#ffc75f,stroke:#333,stroke-width:2px,color:#333
    classDef frontend fill:#ff9671,stroke:#333,stroke-width:2px,color:#333
    classDef devops fill:#00c9a7,stroke:#333,stroke-width:2px,color:#fff
    classDef review fill:#845ec2,stroke:#333,stroke-width:2px,color:#fff
    classDef done fill:#008f7a,stroke:#333,stroke-width:2px,color:#fff

    %% العقد الأساسية
    Start([🚀 بداية الدورة: تحديد المهام]) ::: planning
    
    subgraph GitHub_Project [📋 إدارة المشروع - GitHub Projects]
        direction LR
        Backlog(Backlog) --> Sprint(To Do) --> InProgress(In Progress)
    end

    subgraph Development_Team [💻 فريق التطوير - التنفيذ المتوازي]
        direction TB
        Node[⚙️ 2x Node.js<br>بناء واجهات التخاطب API<br>قواعد البيانات والمنطق] ::: backend
        React[🖥️ 1x React.js<br>لوحات تحكم الإدارة<br>والمدير العام] ::: frontend
        Flutter[📱 3x Flutter<br>تطبيقات الطلاب، أولياء الأمور<br>والمعلمات] ::: frontend
    end

    subgraph Review_Testing [🔍 المراجعة والدمج - GitHub PR]
        direction TB
        PR(إنشاء Pull Request) ::: review
        CodeReview(مراجعة الكود من الفريق) ::: review
        Merge(دمج الكود - Merge to Main) ::: review
    end

    subgraph DevOps_Pipeline [🛠️ مسار التشغيل الآلي - 1x DevOps]
        direction TB
        CI(GitHub Actions<br>فحص واختبار أوتوماتيكي) ::: devops
        CD(رفع التحديثات للسيرفر<br>Staging / Production) ::: devops
    end
    
    End([✅ اكتمال المهمة ووصولها للمستخدم]) ::: done

    %% التوصيلات (المسار)
    Start ==> GitHub_Project
    InProgress ==> Development_Team
    
    Node -.-> |تجهيز الـ API| Flutter & React
    
    Development_Team ==> PR
    PR ==> CodeReview
    CodeReview ==> |موافقة| Merge
    CodeReview -.-> |تعديلات مطلوبة| Development_Team
    
    Merge ==> CI
    CI ==> CD
    CD ==> End
```
