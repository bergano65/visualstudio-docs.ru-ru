---
title: Как включить пользовательскую сборку в компонент BDC | Документация Майкрософт
description: Включите пользовательские сборки в компонент подключения к бизнес-данным, чтобы проект мог ссылаться на сборки из других проектов в том же решении.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a5bce649a0bd9411c064c463defa0946b47e81f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913616"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Как включить пользовательскую сборку в компонент BDC
  Проект может ссылаться на сборки из других проектов в том же решении. Однако эти сборки необходимо добавить в файл компонентов проекта, используя диалоговое окно **назначение упоминаемых сборок в бизнес – системам** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Включение пользовательской сборки в компонент подключения к бизнес-данным (BDC)

1. В **Обозреватель решений** выберите папку, которая содержит модель BDC.

2. В меню **Просмотр** выберите пункт **Окно свойств**.

3. В окне **Свойства** выберите свойство **сборки** и нажмите кнопку с многоточием (![ASP.net Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Эллипс конструктора ASP.NET для мобильных устройств")).

     Откроется диалоговое окно **назначение упоминаемых сборок в бизнес – системам** .

4. В списке **выберите сборку** выберите пользовательскую сборку.

    > [!NOTE]
    > Сборки отображаются в диалоговом окне **назначение упоминаемых сборок в бизнес-системах** , если добавлена ссылка на проект, содержащий сборку. Дополнительные сведения см. в разделе [как добавить или удалить ссылки с помощью диалогового окна "Добавление ссылки"](/previous-versions/wkze6zky(v=vs.140)).

5. В группе **Свойства ссылки** откройте список, который отображается для свойства **область LOBSYSTEM** , выберите бизнес-систему методов, использующих пользовательскую сборку, а затем нажмите кнопку **ОК** .

    > [!NOTE]
    > Для отладки кода в пользовательской сборке необходимо добавить сборку в пакет решения. Дополнительные сведения см. [в разделе инструкции. Добавление и удаление дополнительных сборок](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Практическое руководство. Добавление существующего файла модели подключения к бизнес-данным в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Создание модели подключения к бизнес-данным](../sharepoint/how-to-create-a-bdc-model.md)
- [Интеграгте бизнес-данные в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)