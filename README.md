```mermiad
flowchart TD
    %% --------------------------------------------------------
    %% Class Definitions (توحيد الألوان والتنسيقات)
    %% --------------------------------------------------------
    classDef org fill:#f3e5f5,stroke:#8e24aa,stroke-width:3px,color:#000,font-weight:bold;
    classDef roles fill:#fff3e0,stroke:#e65100,stroke-width:2px,color:#000;
    classDef repo fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px,color:#000;
    classDef board fill:#fff9c4,stroke:#fbc02d,stroke-width:3px,color:#000,font-weight:bold;
    classDef backlog fill:#e3f2fd,stroke:#1e88e5,stroke-width:2px,color:#000;
    classDef columns fill:#f3e5f5,stroke:#8e24aa,stroke-width:2px,color:#000;
    classDef epic fill:#ffcc80,stroke:#e65100,stroke-width:3px,color:#000;
    classDef devops fill:#f9d0c4,stroke:#333,stroke-width:2px,color:#000;
    classDef backend fill:#d4e157,stroke:#333,stroke-width:2px,color:#000;
    classDef frontend fill:#81d4fa,stroke:#333,stroke-width:2px,color:#000;
    classDef mobile fill:#ce93d8,stroke:#333,stroke-width:2px,color:#000;
    classDef gitflow fill:#e8f5e9,stroke:#43a047,stroke-width:2px,color:#000;
    classDef action fill:#fff,stroke:#333,stroke-width:1px,color:#000,stroke-dasharray: 5 5;
    classDef highlight fill:#ffeb3b,stroke:#fbc02d,stroke-width:2px,color:#000;

    %% ========================================================
    %% 1. Org Level
    %% ========================================================
    subgraph Step1_Org [1. مستوى المنظمة وهيكل الفريق - GitHub Organization]
        direction TB
        Org["🏢 منظمة المشروع المركزية <br> School Management System"]:::org
        
        subgraph RolesAccess [هيكل الفريق التقني والإداري]
            direction LR
            PM["مدير المشروع : محمد\nحل المشاكل وتسهيل سير العمل"]:::roles
            DevOpsRole["مطور devops : عمر\nمسؤول عن CI/CD والحماية"]:::roles
            BackendRole["فريق back-end:\nمعتز، لودي"]:::roles
            FlutterRole["فريق flutter:\nمحمد، عمر، سارة"]:::roles
            WebRole["فريق web:\nفيصل"]:::roles
            
            PM --- DevOpsRole --- BackendRole --- FlutterRole --- WebRole
        end
        Org --> RolesAccess
    end

    %% ========================================================
    %% 2. Repos Level
    %% ========================================================
    subgraph Step2_Repos [2. مستوى المستودعات - Polyrepo Architecture]
        direction LR
        R1[📦 Node_Backend]:::repo
        R2[📦 React_Web_Admin]:::repo
        R3[📦 Flutter_Teacher_App]:::repo
        R4[📦 Flutter_Student_App]:::repo
        R5[📦 Flutter_Parent_App]:::repo
    end

    RolesAccess -->|يمنح الصلاحيات ويوزع العمل على| Step2_Repos

    %% ========================================================
    %% 3. Project Management Level
    %% ========================================================
    subgraph Step3_Board [3. إدارة المشروع والمهام - GitHub Project V2]
        direction TB
        BoardTitle["📋 لوحة المهام المركزية الموحدة\n 'Scrum / Kanban Board'"]:::board
        
        subgraph BacklogPhase [مرحلة التخطيط والتحضير]
            direction LR
            PB["📦 Product Backlog\n 'قصص المستخدمين'"]:::backlog
            Grooming["🔍 تنقيح المهام - Backlog Grooming"]:::action
            SprintPlan["🎯 تخطيط السباق - Sprint Planning"]:::highlight
            
            PB --> Grooming --> SprintPlan
        end
        
        BoardTitle --> BacklogPhase

        subgraph KanbanColumns [أعمدة اللوحة ودورة حياة المهمة]
            direction LR
            Todo["📝 Todo\n مهام جاهزة"]:::columns
            InProgress["⏳ In Progress\n قيد التنفيذ"]:::columns
            InReview["👀 In Review\n قيد المراجعة"]:::columns
            Done["✅ Done\n مكتملة ومدمجة"]:::columns
            
            Todo --> InProgress --> InReview --> Done
        end
        
        SprintPlan -->|سحب وتوزيع المهام على| Todo
    end

    Step2_Repos -->|جميع المستودعات تغذي اللوحة بالمهام| BoardTitle

    %% ========================================================
    %% 4. Execution Level (Epics & Sprints)
    %% ========================================================
    subgraph Step4_Execution [4. التنفيذ البرمجي - Epics & Sprints]
        direction TB
        Epic1[🔐 Epic 1: Identity & Access Management <br> نظام المصادقة والصلاحيات]:::epic
        
        subgraph Sprint1 [المرحلة الأولى: التأسيس والعمل المتوازي - Sprint 1]
            direction TB
            A[⚙️ DevOps: إعداد بيئة CI/CD وقواعد البيانات]:::devops
            
            subgraph Backend_Team [🌐 فريق Node.js - 2 مطورين]
                B1[تصميم Mock APIs ونماذج المستخدمين]:::backend
                B2[تطوير منطق الإدارة والمعلمين]:::backend
                B3[تطوير منطق الطلاب وأولياء الأمور]:::backend
                B1 --> B2 & B3
            end

            A --> Backend_Team

            subgraph Frontend_Web [💻 فريق React.js - 1 مطور]
                C1[شاشة Login وحماية المسارات - ويب]:::frontend
            end

            subgraph Mobile_Team [📱 فريق Flutter - 3 مطورين]
                D1[Login تطبيق المعلمة والمدير]:::mobile
                D2[Login تطبيق الطالب]:::mobile
                D3[Login تطبيق ولي الأمر]:::mobile
            end

            Backend_Team -.->|1. عقود API للعمل المتوازي| C1
            Backend_Team -.->|2. عقود API للعمل المتوازي| D1
            Backend_Team -.->|3. عقود API للعمل المتوازي| D2
            Backend_Team -.->|4. عقود API للعمل المتوازي| D3
        end
        
        Epic1 --> Sprint1
    end

    KanbanColumns -->|تنفيذ مهام الـ Sprint الحالي| Epic1

    %% ========================================================
    %% 5. Git Workflow Level
    %% ========================================================
    subgraph Step5_GitFlow [5. دورة حياة الكود اليومية - Strict Git Flow & PR Cycle]
        direction TB
        
        DevBranch((🌿 Develop Branch\n فرع الاختبار والتجميع)):::gitflow
        
        subgraph DeveloperDaily [عمل المطور اليومي]
            direction TB
            TaskAction[📋 سحب مهمة من Todo\n وإنشاء فرع جديد feature/login]:::action
            CodeAction[💻 كتابة الكود محلياً\n وعمل Commits واضحة]:::action
            PushAction[☁️ رفع الفرع إلى\n مستودع GitHub]:::action
            
            TaskAction --> CodeAction --> PushAction
        end
        
        DevBranch -->|تفرع للبدء بمهمة| TaskAction

        subgraph PullRequestCycle [دورة المراجعة والدمج - PR]
            direction TB
            OpenPR[📝 فتح Pull Request\n للدمج مع فرع Develop]:::action
            ReviewFlow[🔍 مراجعة الكود Code Review\n موافقة المراجع (Approve)]:::action
            CIFlow[⚙️ الفحص الآلي CI/CD\n للتأكد من خلو الأخطاء]:::action
            MergeFlow[✅ دمج الكود Merge\n وحذف فرع المهمة]:::highlight
            
            OpenPR --> ReviewFlow --> CIFlow --> MergeFlow
        end
        
        PushAction --> OpenPR
        MergeFlow -->|تحديث مستمر للفرع الأساسي| DevBranch
        MergeFlow -.->|⚡ أتمتة: نقل حالة المهمة إلى Done| Done
    end

    Sprint1 -->|تطبيق المهام عبر نظام النسخ| DevBranch
```
