---
title: Символ поставщика | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d54494a8fa23e0714769863ac0fa2e5ddc1f4c2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276979"
---
# <a name="symbol-provider"></a>Поставщик символов
Реализация вычислителя выражений необходимо получить доступ к символической отладочной информации, создаваемой компилятором языка для оценки переменных и выражений. Это достигается путем использования интерфейсы поставщика символов (SP), также вызывается обработчик символов.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] SPs предоставляет для управляемого кода, а также машинного кода, в формате базы данных программы (PDB) символов. При отсутствии надежный, необходимые для вашей программы символов, хранящихся в пользовательском формате, это рекомендуется использовать пакеты обновления, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчиков ожидать, что дает возможность общаться с SPs, с помощью интерфейсов Common Language Runtime (CLR). Таким образом SP, который будет использоваться механизмы отладки Visual Studio должна поддерживать среды CLR. Полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, входящий в состав из [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Если ваш пакет будет работать только с вашего пользовательского модуля отладки, можно реализовать SP по своему усмотрению в зависимости от потребностей вашего модуля отладки.  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)