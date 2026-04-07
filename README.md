
```mermaid
flowchart TD
    classDef devops fill:#f9d0c4,stroke:#333,stroke-width:2px,color:#000;
    classDef backend fill:#d4e157,stroke:#333,stroke-width:2px,color:#000;
    classDef frontend fill:#81d4fa,stroke:#333,stroke-width:2px,color:#000;
    classDef mobile fill:#ce93d8,stroke:#333,stroke-width:2px,color:#000;

    subgraph Phase1 [المرحلة الأولى: التأسيس والعمل المتوازي - Sprint 1]
        direction TB
        
        A[⚙️ DevOps 1x <br> إعداد بيئة CI/CD وقواعد البيانات]:::devops
        
        subgraph Backend_Team [🌐 فريق Node.js - 2 مطورين]
            B1[تصميم Mock APIs لجميع الحسابات]:::backend
            B2[تطوير منطق الإدارة والمعلمين]:::backend
            B3[تطوير منطق الطلاب وأولياء الأمور]:::backend
            B1 --> B2 & B3
        end

        A --> B1

        subgraph Frontend_Web [💻 فريق React.js - 1 مطور]
            C1[لوحة تحكم المدير/الإداري - ويب]:::frontend
        end

        subgraph Mobile_Team [📱 فريق Flutter - 3 مطورين]
            D1[تطبيق المعلمة والمدير]:::mobile
            D2[تطبيق الطالب]:::mobile
            D3[تطبيق ولي الأمر]:::mobile
        end

        B1 -.->|1. عقود API وهمية للعمل المتوازي| C1
        B1 -.->|2. عقود API وهمية للعمل المتوازي| D1
        B1 -.->|3. عقود API وهمية للعمل المتوازي| D2
        B1 -.->|4. عقود API وهمية للعمل المتوازي| D3
    end
```
