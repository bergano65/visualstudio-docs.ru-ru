---
title: VBA и решений Office в Visual Studio по сравнению | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5a92727f08729fc7f8a871d0528c9e652d92f8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Сравнение решений Office и VBA в Visual Studio
  В Microsoft Visual Basic для приложений (VBA) используется неуправляемый код, который тесно интегрирован с приложениями Office. Проекты Microsoft Office, созданные с помощью Visual Studio, позволяют воспользоваться преимуществами платформы .NET Framework и средств разработки Visual Studio.  
  
 Сведения о типах решений Office, можно создать с помощью Visual Studio см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Оператор  
 В следующей таблице приводится общее сравнение решений VBA и решений Office в Visual Studio.  
  
|Решения VBA|Решения Office в Visual Studio|  
|-------------------|---------------------------------------|  
|Использует код, который связан с конкретным документом и сохраняется с ним.|Использует код, который хранится отдельно от документа (для настроек на уровне документа) или в сборке, которая загружается приложением (для надстроек VSTO).|  
|Работает с объектными моделями Office и программными интерфейсами VBA.|Предоставляет доступ к объектным моделям Office и API-интерфейсам [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|  
|Предназначен для записи макросов и упрощения процесса разработки.|Предназначен для обеспечения безопасности, упрощения поддержки кода и использования полной интегрированной среды разработки (IDE) Visual Studio.|  
|Подходит для решений, которые получают преимущества от тесной интеграции с приложениями Office.|Подходит для решений, которые получают преимущества от полных ресурсов Visual Studio и [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Имеет ограничения при использовании на предприятиях, особенно в области безопасности и развертывания.|Предназначен для использования на предприятиях.|  
  
 Некоторые задачи по-прежнему проще и быстрее выполнить с помощью VBA. В частности, VBA может быть необходимо использовать для:  
  
-   настраиваемых функций для работы с листами.  
  
-   записи макросов.  
  
## <a name="combining-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Объединение решений VBA и решений Office, созданных с помощью Visual Studio  
 Код VBA можно вызывать из решений Office, созданных с помощью Visual Studio. Также можно вызывать код в решениях Office, созданных с помощью Visual Studio, из VBA. Конкретная методика зависит от того, является ли ваше решение Office надстройкой VSTO или настройкой на уровне документа. Дополнительные сведения см. в разделах [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) и [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Объединение настроек VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)   
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Приступая к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  