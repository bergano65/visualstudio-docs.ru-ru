---
title: Не удается удалить свойство
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 80b5e40900cd8912b727270a46ebcf119c324f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922871"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Свойство \<имя свойства > не может быть удалена

Свойство \<имя свойства > нельзя удалить, поскольку он задан как **Свойство дискриминатора** для наследования между \<имя класса > и \<имя класса >

Выбранное свойство имеет значение **Свойство дискриминатора** для наследования между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в конфигурации наследования между классами данных.

Задать **Свойство дискриминатора** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. В реляционном конструкторе объектов выберите линию наследования, которая соединяет классы данных, указанные в сообщении об ошибке.

2. Задать **дискриминатора** свойство другое свойство.

3. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)