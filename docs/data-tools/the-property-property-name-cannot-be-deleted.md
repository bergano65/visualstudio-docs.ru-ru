---
title: Невозможно удалить свойство
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 63e99bf7b247856815fd3e8de0f4932fed4881dc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535295"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Невозможно удалить свойство \<property name>

Свойство \<property name> не может быть удалено, так как оно задано как **Свойство дискриминатора** для наследования между \<class name> и\<class name>

Выбранное свойство назначено в качестве **свойства дискриминатора** для наследования между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в конфигурации наследования между классами данных.

Установите в качестве **свойства дискриминатора** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. В **конструкторе O/R**выберите линию наследования, соединяющую классы данных, указанные в сообщении об ошибке.

2. Задайте в качестве свойства **дискриминатора** другое свойство.

3. Попытайтесь снова удалить свойство.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)