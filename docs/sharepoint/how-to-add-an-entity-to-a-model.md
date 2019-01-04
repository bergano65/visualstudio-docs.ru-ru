---
title: Как выполнить Добавление сущности в модель | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 347728ac4f096359f06ca7823adfcd1b25ff527a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964038"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Как выполнить Добавление сущности в модель
  Чтобы создать сущность, добавьте элемент управления сущности из Visual Studio **элементов** в конструктор бизнес-данным (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Чтобы добавить сущность в модель  
  
1.  Создание проекта BDC, или откройте существующий проект BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  В **элементов**, из **каталог бизнес-данных** группу, добавить **сущности** элемента управления в конструктор.  
  
     В конструкторе отобразится новая сущность. Visual Studio добавляет `<Entity>` элемент к XML-файла модели BDC в проекте. Дополнительные сведения об атрибутах элемента сущности, см. в разделе [сущности](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  В конструкторе, откройте контекстное меню для сущности, выберите **добавить**, а затем выберите **идентификатор**.  
  
     Отобразится новый идентификатор для сущности.  
  
    > [!NOTE]  
    >  Можно изменить имя сущности и идентификатора в **свойства** окна.  
  
4.  Определение полей сущности в классе. Можно добавить новый класс в проект или использовать существующий класс, созданный с помощью других средств, таких как реляционный конструктор объектов (O/R Designer). Следующий пример показывает класс сущностей с именем контакта.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>См. также
 [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)  
