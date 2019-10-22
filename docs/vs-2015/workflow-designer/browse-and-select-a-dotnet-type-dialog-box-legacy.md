---
title: Диалоговое окно "Обзор и выбор типа .NET" (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668977"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Диалоговое окно «Обзор и выбор типа .NET» (для прежних версий)
В этом разделе описывается использование диалогового окна **Обзор и выбор типа .NET** в [!INCLUDE[wfd1](../includes/wfd1-md.md)] устаревших версий. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 В окне **Свойства** при выборе свойств, которые принимают тип .NET Framework в упоминаемой сборке, в конце текстового поля свойства появляется многоточие **[...]** . Если щелкнуть **[...]** , откроется диалоговое окно **Обзор и выбор типа .NET** . В этом диалоговом окне из представления в виде дерева сборок, на которые есть ссылки, можно выбрать тип. Например, при использовании конструктора действий в окне **Свойства** щелкните **базовый класс** многоточие **[...]** , чтобы выбрать другой базовый класс для действия из дерева сборок, на которое указывает ссылка.

 В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **Обзор и выбор типа .NET** .

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Имя типа:**|Имя выбранного в данный момент типа.|
|**Type**|Левая панель содержит представление в виде дерева сборок, на которые есть ссылки. Правая панель содержит типы, доступные для выделения из сборки, на которую есть ссылка, выбранной в левой панели.|

## <a name="see-also"></a>См. также раздел
 [Использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)