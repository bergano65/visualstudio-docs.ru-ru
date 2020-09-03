---
title: '&lt;Имя свойства свойства &gt; не может быть удалено | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667240"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>&lt; &gt; Не удается удалить имя свойства свойства
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Свойство \<property name> не может быть удалено, так как оно задано как свойство дискриминатора для наследования между \<class name> и \<class name>

 Выбранное свойство назначено в качестве **свойства дискриминатора** для наследования между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в конфигурации наследования между классами данных.

 Установите в качестве **свойства дискриминатора** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. В реляционном конструкторе объектов выберите линию наследования, которая соединяет классы данных, указанные в сообщении об ошибке.

2. Задайте в качестве свойства **дискриминатора** другое свойство.

3. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также:
 [Практическое руководство. Настройка наследования с помощью наследования классов данных в конструкторе o/](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) r [(конструктор o/r Designer)](../data-tools/data-class-inheritance-o-r-designer.md) [Пошаговое руководство. Создание LINQ to SQL классов с помощью наследования одной таблицы (реляционный конструктор r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
