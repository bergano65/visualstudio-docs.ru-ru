---
title: Символ поставщика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea31d6bcd8c055756a49c46f8fb4b3f377aaade8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912903"
---
# <a name="symbol-provider"></a>Поставщик символов
Реализация вычислителя выражений необходимо получить доступ к символической отладочной информации, создаваемой компилятором языка для оценки переменных и выражений. Это достигается путем использования интерфейсы поставщика символов (SP), также вызывается обработчик символов.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] SPs предоставляет для управляемого кода, а также машинного кода, в формате базы данных программы (PDB) символов. При отсутствии надежный, необходимые для вашей программы символов, хранящихся в пользовательском формате, это рекомендуется использовать пакеты обновления, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Примечания по реализации
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчиков ожидать, что дает возможность общаться с SPs, с помощью интерфейсов Common Language Runtime (CLR). Таким образом SP, который будет использоваться механизмы отладки Visual Studio должна поддерживать среды CLR. Полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, входящий в состав из [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Если ваш пакет будет работать только с вашего пользовательского модуля отладки, можно реализовать SP по своему усмотрению в зависимости от потребностей вашего модуля отладки.

## <a name="see-also"></a>См. также
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)