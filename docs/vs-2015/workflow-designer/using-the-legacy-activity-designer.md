---
title: Using the Legacy Activity Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302826"
---
# <a name="using-the-legacy-activity-designer"></a>Использование конструктора действия для прежних версий
В данном разделе описано использование конструктора действий в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] более ранней версии. Используйте конструктор более ранней версии, если приложение должно ориентироваться на [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Конструктор действий позволяет создавать собственные пользовательские действия.

## <a name="creating-a-custom-activity"></a>Создание пользовательского действия
 Для создания пользовательского действия с помощью конструктора действий выполните следующие шаги:

1. On the **Project** menu, click **Add Activity**.

2. Select the **Activity** or **Activity (with code separation)** template.

   1. Use the **Activity** template to create an activity with the activity definition and the user code in same code file.

   2. Use the **Activity (with code separation)** template to create an activity with the activity definition expressed as workflow markup and the user code in a separate code file.

3. Type an activity name or keep the default name, and then click **Add**.

   You can also create a set of custom activities by creating a new project of type **Workflow Activity Library**. For more information about this project type, see [How to: Create a Workflow Activity Library (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Настройка действия
 Пока конструктор действия активен, для настройки свойств, перечисленных в следующей таблицы, можно использовать браузер свойств.

|свойство;|Комментарии|
|--------------|--------------|
|**Name**|Имя действия.|
|**Base Class**|Базовый класс от которого наследуется действие. The default base class is [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). In the **Properties** window, click the **Base Class** ellipses **[…]** to select another base class in the [Browse and Select a .NET Type Dialog Box (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Описание**|Пользовательское описание действия.|
|**Enabled**|Set to **True** by default to enable activity execution and validation. Set to **False** to disable activity execution and validation. For information about activity execution and validation, see [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Добавление дочерних действий
 Можно перетащить дочерние действия с панели элементов на разрабатываемое действие. Далее, используя браузер свойств, можно настроить каждое дочернее действие.

## <a name="see-also"></a>См. также раздел
 [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65024) [Creating Custom Activities](https://go.microsoft.com/fwlink?LinkID=65021) [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md) [Custom Activities Samples](https://go.microsoft.com/fwlink?LinkID=65022) [How to: Create a Workflow Activity Library (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [Using the Legacy Workflow Designer](../workflow-designer/using-the-legacy-workflow-designer.md)