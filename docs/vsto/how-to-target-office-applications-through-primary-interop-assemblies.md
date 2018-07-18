---
title: 'Как: Office целевых приложений с помощью основных сборок взаимодействия'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32ff157e3986836ac13472c4a9ed8a7b01f06e04
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262516"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Как: Office целевых приложений с помощью основных сборок взаимодействия
  При создании нового проекта Office Visual Studio автоматически добавляет ссылки на основные сборки взаимодействия (PIA) Microsoft Office, необходимые для построения проекта. Ссылки на другие основные сборки взаимодействия необходимо добавлять в следующих случаях.  
  
-   Вы хотите использовать функции других приложений Microsoft Office в своем проекте. Например, можно использовать функции Microsoft Office Excel в проекте для Microsoft Office Word.  
  
-   Вы хотите автоматизировать приложения Microsoft Office, у которых нет выделенных проектов в Visual Studio, например Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Добавление ссылки на основную сборку взаимодействия  
  
1.  Откройте проект Office и выберите имя проекта в **обозревателе решений**.  
  
2.  В меню **Проект** щелкните команду **Добавить ссылку**.  
  
3.  На **Framework** выберите основной сборки ВЗАИМОДЕЙСТВИЯ в **имя компонента** списка. Дополнительные сведения о доступных основных сборках взаимодействия Microsoft Office см. в разделе [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
     Если проект предназначен [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, **внедрить типы взаимодействия** для ссылки на сборку свойству **True** по умолчанию. Благодаря применению этого параметра вашему решению на компьютерах конечных пользователей основная сборка взаимодействия не требуется. Дополнительные сведения см. в разделе [разработки и создавать решения Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  В проектах Office всегда добавляйте ссылки на основные сборки взаимодействия Office с помощью **.NET** вкладке **добавить ссылку** диалоговое окно, а не **COM** вкладки. Дополнительные сведения см. в разделе [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Нажмите кнопку **ОК**.  
  
     Имя сборки появляется в **ссылки** папки **обозревателе решений**.  
  
## <a name="see-also"></a>См. также  
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Напишите код в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Разработки решений Office](../vsto/developing-office-solutions.md)   
 [Как: установить основные сборки взаимодействия](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  