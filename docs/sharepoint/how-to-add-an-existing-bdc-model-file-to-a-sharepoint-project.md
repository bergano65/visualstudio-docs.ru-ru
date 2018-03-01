---
title: "Как: Добавление существующего файла модели BDC в проект SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f5f13377211a6b8a7a2035d85e1423be9d2bbb72
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Практическое руководство. Добавление существующего файла модели подключения к бизнес-данным в проект SharePoint
  Вы можете настраивать, упаковывать и повторно развертывать модель подключения к бизнес-данным (BDC) с помощью Visual Studio для добавления файла модели (.bdcm) к любому проекту фермы SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Добавление файла модели подключения к бизнес-данным (BDC) в проект SharePoint  
  
1.  В **обозревателе решений**, выберите папку для проекта SharePoint.  
  
2.  В строке меню выберите **проекта**, **Добавление существующего элемента**.  
  
3.  В **Добавление существующего элемента** диалоговое окно, перейдите к расположению файла определения модели, которую требуется добавить в проект, выберите файл и нажмите кнопку **добавить** кнопки.  
  
     Если модель не определяет *строке из БИЗНЕС-систему типа сборки .NET*, **бизнес-системы сборки .NET, добавьте** откроется диалоговое окно.  
  
4.  Если появится диалоговое окно, выполните одно из следующих действий.  
  
    -   Если вы хотите создавать пользовательский код и использовать конструктор для определения метаданных для импортированной модели, выберите **Да** , назовите систему, а затем щелкните **ОК** кнопки.  
  
    -   В противном случае выберите **нет** , а затем кнопку **ОК** кнопки.  
  
     **Модель подключения к бизнес-данным** элемент добавляется в проект.  
  
## <a name="see-also"></a>См. также  
 [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Как: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Как: определить локализованные имена, свойства и разрешения с помощью файла ресурсов](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Как: Добавление пользовательской сборки в функцию BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  