---
title: Целевые приложения Office через основные сборки взаимодействия
description: Узнайте, как можно использовать Visual Studio для программного назначения Microsoft Office приложений с помощью основных сборок взаимодействия.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 81c2852a92124a7cf9fb6078b196982d22100be7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528099"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Пошаговое руководство. Назначение приложений Office через основные сборки взаимодействия
  При создании нового проекта Office Visual Studio автоматически добавляет ссылки на основные сборки взаимодействия (PIA) Microsoft Office, необходимые для построения проекта. Ссылки на другие основные сборки взаимодействия необходимо добавлять в следующих случаях.

- Вы хотите использовать функции других приложений Microsoft Office в своем проекте. Например, можно использовать функции Microsoft Office Excel в проекте для Microsoft Office Word.

- Вы хотите автоматизировать приложения Microsoft Office, у которых нет выделенных проектов в Visual Studio, например Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Добавление ссылки на основную сборку взаимодействия

1. Откройте проект Office и выберите имя проекта в **Обозреватель решений**.

2. В меню **Проект** выберите пункт **Добавить ссылку**.

3. На вкладке **платформа** выберите нужную сборку PIA в списке **имя компонента** . Дополнительные сведения о доступных Microsoft Office основных сборках взаимодействия см. в разделе [основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

     Если проект предназначен для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, свойство **Внедрить типы взаимодействия** для ссылки на сборку по умолчанию имеет значение **true** . Благодаря применению этого параметра вашему решению на компьютерах конечных пользователей основная сборка взаимодействия не требуется. Дополнительные сведения см. в статье [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > В проектах Office всегда добавляйте ссылки на основные сборки взаимодействия Office, используя вкладку **.NET** диалогового окна **Добавление ссылки** , а не на вкладку **com** . Дополнительные сведения см. в разделе [основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

4. Нажмите кнопку **ОК**.

     Имя сборки отображается в папке **references** **Обозреватель решений**.

## <a name="see-also"></a>См. также раздел
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
