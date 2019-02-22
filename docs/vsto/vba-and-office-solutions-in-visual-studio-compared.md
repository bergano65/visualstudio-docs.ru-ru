---
title: Решения VBA и Office в Visual Studio по сравнению с
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d97ff0b7e11bf79a8da6f3e034227c66ae1f9189
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618332"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Решения VBA и Office в Visual Studio по сравнению с
  В Microsoft Visual Basic для приложений (VBA) используется неуправляемый код, который тесно интегрирован с приложениями Office. Проекты Microsoft Office, созданные с помощью Visual Studio, позволяют воспользоваться преимуществами платформы .NET Framework и средств разработки Visual Studio.

 Сведения о типах решений Office, которые можно создавать с помощью Visual Studio, см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Сравнение
 В следующей таблице приводится общее сравнение решений VBA и решений Office в Visual Studio.

|Решения VBA|Решения Office в Visual Studio|
|-------------------|---------------------------------------|
|Использует код, который связан с конкретным документом и сохраняется с ним.|Использует код, который хранится отдельно от документа (для настроек уровня документа), или в сборке, которая загружается приложением (для надстроек VSTO).|
|Работает с объектными моделями Office и программными интерфейсами VBA.|Предоставляет доступ к объектным моделям Office и API-интерфейсам [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Предназначен для записи макросов и упрощения процесса разработки.|Предназначен для обеспечения безопасности, упрощения поддержки кода и использования полной интегрированной среды разработки (IDE) Visual Studio.|
|Подходит для решений, которые получают преимущества от тесной интеграции с приложениями Office.|Подходит для решений, которые получают преимущества от полных ресурсов Visual Studio и [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|
|Имеет ограничения при использовании на предприятиях, особенно в области безопасности и развертывания.|Предназначен для использования на предприятиях.|

 Некоторые задачи по-прежнему проще и быстрее выполнить с помощью VBA. В частности, VBA может быть необходимо использовать для:

-   настраиваемых функций для работы с листами.

-   записи макросов.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Объединение решений VBA и решений Office, созданных с помощью Visual Studio
 Код VBA можно вызывать из решений Office, созданных с помощью Visual Studio. Также можно вызывать код в решениях Office, созданных с помощью Visual Studio, из VBA. Конкретная методика зависит от того, является ли ваше решение Office надстройкой VSTO или настройкой на уровне документа. Дополнительные сведения см. в разделе [вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) и [объединение VBA и настроек уровня документа](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>См. также
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Объединение VBA и настроек уровня документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)
- [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
