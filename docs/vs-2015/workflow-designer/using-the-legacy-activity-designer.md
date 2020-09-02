---
title: Использование конструктора устаревших действий | Документация Майкрософт
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
ms.openlocfilehash: cd8d18d95fabd858354c625d2c9b32459efc7193
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846142"
---
# <a name="using-the-legacy-activity-designer"></a>Использование конструктора действия для прежних версий
В данном разделе описано использование конструктора действий в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] более ранней версии. Используйте конструктор более ранней версии, если приложение должно ориентироваться на [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Конструктор действий позволяет создавать собственные пользовательские действия.

## <a name="creating-a-custom-activity"></a>Создание пользовательского действия
 Для создания пользовательского действия с помощью конструктора действий выполните следующие шаги:

1. В меню **проект** выберите команду **Добавить действие**.

2. Выберите шаблон **действие** или **действие (с разделением кода)** .

   1. Используйте шаблон **действия** для создания действия с определением действия и пользовательским кодом в одном файле кода.

   2. Используйте шаблон **действие (с разделением кода)** для создания действия с определением действия, выраженное в виде разметки рабочего процесса, и пользовательского кода в отдельном файле кода.

3. Введите имя действия или сохраните имя по умолчанию, а затем нажмите кнопку **Добавить**.

   Вы также можете создать набор настраиваемых действий, создав новый проект типа **Библиотека действий рабочих процессов**. Дополнительные сведения об этом типе проекта см. [в разделе инструкции. Создание библиотеки действий рабочего процесса (устаревшая)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Настройка действия
 Пока конструктор действия активен, для настройки свойств, перечисленных в следующей таблицы, можно использовать браузер свойств.

|Свойство|Комментарии|
|--------------|--------------|
|**Имя**|Имя действия.|
|**Базовый класс**|Базовый класс от которого наследуется действие. Базовым классом по умолчанию является [SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx). В окне **Свойства** щелкните **базовый класс** многоточие **[...]** , чтобы выбрать другой базовый класс в [диалоговом окне Обзор и выбор типа .NET (прежние версии)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Описание**|Пользовательское описание действия.|
|**Включен**|Установите значение **true** по умолчанию, чтобы включить выполнение и проверку действия. Задайте значение **false** , чтобы отключить выполнение и проверку действия. Сведения о выполнении и проверке действий см. в разделе [Разработка действий рабочего процесса](https://msdn2.microsoft.com/library/ms734413.aspx).|

## <a name="adding-child-activities"></a>Добавление дочерних действий
 Можно перетащить дочерние действия с панели элементов на разрабатываемое действие. Далее, используя браузер свойств, можно настроить каждое дочернее действие.

## <a name="see-also"></a>См. также:
 [Разработка действий рабочего процесса](https://msdn2.microsoft.com/library/ms734413.aspx) [Создание настраиваемых действий](https://msdn2.microsoft.com/library/bb675228.aspx) [устаревшие действия рабочих процессов](../workflow-designer/legacy-workflow-activities.md) [примеры](https://msdn2.microsoft.com/library/bb472471.aspx) действий [: создание библиотеки действий рабочего процесса (устаревшая)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [с помощью устаревшей конструктор рабочих процессов](../workflow-designer/using-the-legacy-workflow-designer.md)
