---
title: Как добавить существующий файл модели BDC в проект SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92063b5aeaf4f86919b9eabf783b102a9f5b8f34
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016525"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Как добавить существующий файл модели BDC в проект SharePoint
  Вы можете настраивать, упаковывать и повторно развертывать модель подключения к бизнес-данным с помощью Visual Studio, добавляя файл модели (*бдкм*) в любой проект фермы SharePoint. Дополнительные сведения см. [в статье Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Добавление файла модели подключения к бизнес-данным (BDC) в проект SharePoint

1. В **Обозреватель решений**выберите папку для проекта SharePoint.

2. В строке меню выберите **проект**  >  **Добавить существующий элемент**.

3. В диалоговом окне **Добавление существующего элемента** перейдите к расположению файла определения модели, который необходимо добавить в проект, выберите файл и нажмите кнопку **Добавить** .

    Если в модели не определена *Бизнес-система типа "сборка .NET*", откроется диалоговое окно **Добавление системы LobSystem для сборки .NET** .

4. Если появится диалоговое окно, выполните одно из следующих действий.

   - Если вы хотите написать пользовательский код и использовать конструктор для определения метаданных для импортированной модели, нажмите кнопку **Да** , присвойте имя системе, а затем нажмите кнопку **ОК** .

   - В противном случае нажмите кнопку **нет** , а затем нажмите кнопку **ОК** .

     Элемент **модели подключения к бизнес-данным** добавляется в проект.

## <a name="see-also"></a>См. также раздел
- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Как создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Как использовать файл ресурсов для указания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Как включить пользовательскую сборку в компонент BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
