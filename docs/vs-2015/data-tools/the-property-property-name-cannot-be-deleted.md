---
title: Не удается удалить свойство &lt;property имя &gt; | Документация Майкрософт
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667240"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Не удается удалить свойство &lt;property имя &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Не удается удалить свойство \<property name >, так как оно задано как свойство дискриминатора для наследования между \<class name > и \<class name >

 Выбранное свойство назначено в качестве **свойства дискриминатора** для наследования между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в конфигурации наследования между классами данных.

 Установите в качестве **свойства дискриминатора** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. В реляционном конструкторе объектов выберите линию наследования, которая соединяет классы данных, указанные в сообщении об ошибке.

2. Задайте в качестве свойства **дискриминатора** другое свойство.

3. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также раздел
 [Практическое руководство. Настройка наследования с помощью наследования классов данных в конструкторе o/](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) r [(конструктор o/r Designer)](../data-tools/data-class-inheritance-o-r-designer.md) [Пошаговое руководство. Создание LINQ to SQL классов с помощью наследования одной таблицы (реляционный конструктор r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
