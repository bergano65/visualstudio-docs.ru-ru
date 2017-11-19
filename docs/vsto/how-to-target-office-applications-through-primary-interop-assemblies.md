---
title: "Как: обращение к приложениям Office с помощью основных сборок взаимодействия | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a96ec16afda8823ddf9918340498e29efdff2f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>How to: Target Office Applications Through Primary Interop Assemblies
  При создании нового проекта Office Visual Studio автоматически добавляет ссылки на основные сборки взаимодействия (PIA) Microsoft Office, необходимые для построения проекта. Ссылки на другие основные сборки взаимодействия необходимо добавлять в следующих случаях.  
  
-   Вы хотите использовать функции других приложений Microsoft Office в своем проекте. Например, можно использовать функции Microsoft Office Excel в проекте для Microsoft Office Word.  
  
-   Вы хотите автоматизировать приложения Microsoft Office, у которых нет выделенных проектов в Visual Studio, например Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Добавление ссылки на основную сборку взаимодействия  
  
1.  Откройте проект Office и выберите имя проекта в **обозревателе решений**.  
  
2.  В меню **Проект** щелкните команду **Добавить ссылку**.  
  
3.  На **Framework** выберите основной сборки ВЗАИМОДЕЙСТВИЯ в **имя компонента** списка. Дополнительные сведения о доступных основных сборках взаимодействия Microsoft Office см. в разделе [основных сборках взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
     Если проект предназначен [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, **внедрить типы взаимодействия** для ссылки на сборку свойству **True** по умолчанию. Благодаря применению этого параметра вашему решению на компьютерах конечных пользователей основная сборка взаимодействия не требуется. Дополнительные сведения см. в разделе [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  В проектах Office всегда добавляйте ссылки на основные сборки взаимодействия Office с помощью **.NET** вкладке **добавить ссылку** диалоговое окно, а не **COM** вкладки. Дополнительные сведения см. в разделе [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Нажмите кнопку **ОК**.  
  
     Имя сборки появляется в **ссылки** папки **обозревателе решений**.  
  
## <a name="see-also"></a>См. также  
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Практическое руководство. Установка основных сборок взаимодействия Microsoft Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  