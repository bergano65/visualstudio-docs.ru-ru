---
title: Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 074b01e78fd398a43548febf81ba03b61a8646b4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079640"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия
  При создании нового проекта Office Visual Studio автоматически добавляет ссылки на основные сборки взаимодействия (PIA) Microsoft Office, необходимые для построения проекта. Ссылки на другие основные сборки взаимодействия необходимо добавлять в следующих случаях.

- Вы хотите использовать функции других приложений Microsoft Office в своем проекте. Например, можно использовать функции Microsoft Office Excel в проекте для Microsoft Office Word.

- Вы хотите автоматизировать приложения Microsoft Office, у которых нет выделенных проектов в Visual Studio, например Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Добавление ссылки на основную сборку взаимодействия

1. Откройте проект Office и выберите имя проекта в **обозревателе решений**.

2. В меню **Проект** щелкните команду **Добавить ссылку**.

3. На **Framework** выберите в основных сборках ВЗАИМОДЕЙСТВИЯ **имя компонента** списка. Дополнительные сведения о доступных основных сборках взаимодействия Microsoft Office, см. в разделе [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

     Если проект предназначен [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, **Embed Interop Types** для ссылки на сборку свойству **True** по умолчанию. Благодаря применению этого параметра вашему решению на компьютерах конечных пользователей основная сборка взаимодействия не требуется. Дополнительные сведения см. в разделе [проектирования и создания решений Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    >  В проектах Office всегда добавляйте ссылки на основные сборки взаимодействия Office с помощью **.NET** вкладке **добавить ссылку** диалоговое окно, а не **COM** вкладки. Дополнительные сведения см. в разделе [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

4. Нажмите кнопку **ОК**.

     Имя сборки появляется в **ссылки** папке **обозревателе решений**.

## <a name="see-also"></a>См. также
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Практическое руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
