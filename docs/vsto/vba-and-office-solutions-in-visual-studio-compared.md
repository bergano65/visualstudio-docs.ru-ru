---
title: "Сравнение решений Office и VBA в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "код VBA, расширения управляемого кода"
  - "расширения управляемого кода [разработка решений Office в Visual Studio], VBA в сравнении с "
ms.assetid: 31756c2f-8829-4011-ad77-134cb3728344
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Сравнение решений Office и VBA в Visual Studio
  В Microsoft Visual Basic для приложений \(VBA\) используется неуправляемый код, который тесно интегрирован с приложениями Office. Проекты Microsoft Office, созданные с помощью Visual Studio, позволяют воспользоваться преимуществами платформы .NET Framework и средств разработки Visual Studio.  
  
 Сведения о типах решений Office, которые можно создавать с помощью Visual Studio, см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## Оператор  
 В следующей таблице приводится общее сравнение решений VBA и решений Office в Visual Studio.  
  
|Решения VBA|Решения Office в Visual Studio|  
|-----------------|------------------------------------|  
|Использует код, который связан с конкретным документом и сохраняется с ним.|Использует код, который хранится отдельно от документа \(для настроек на уровне документа\) или в сборке, которая загружается приложением \(для надстроек VSTO\).|  
|Работает с объектными моделями Office и программными интерфейсами VBA.|Предоставляет доступ к объектным моделям Office и API\-интерфейсам [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Предназначен для записи макросов и упрощения процесса разработки.|Предназначен для обеспечения безопасности, упрощения поддержки кода и использования полной интегрированной среды разработки \(IDE\) Visual Studio.|  
|Подходит для решений, которые получают преимущества от тесной интеграции с приложениями Office.|Подходит для решений, которые получают преимущества от полных ресурсов Visual Studio и [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Имеет ограничения при использовании на предприятиях, особенно в области безопасности и развертывания.|Предназначен для использования на предприятиях.|  
  
 Некоторые задачи по\-прежнему проще и быстрее выполнить с помощью VBA. В частности, VBA может быть необходимо использовать для:  
  
-   настраиваемых функций для работы с листами.  
  
-   записи макросов.  
  
## Объединение решений VBA и решений Office, созданных с помощью Visual Studio  
 Код VBA можно вызывать из решений Office, созданных с помощью Visual Studio. Также можно вызывать код в решениях Office, созданных с помощью Visual Studio, из VBA. Конкретная методика зависит от того, является ли ваше решение Office надстройкой VSTO или настройкой на уровне документа. Дополнительные сведения см. в разделах [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) и [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).  
  
## См. также  
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)   
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  