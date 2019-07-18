---
title: Интерфейс IProvideExpressionContexts | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410036"
---
# <a name="iprovideexpressioncontexts-interface"></a>Интерфейс IProvideExpressionContexts
Предоставляет способ для перечисления контекстов выражений, известных по определенному компоненту. Этот интерфейс обычно реализуется обработчиков сценариев.  
  
 Диспетчер отладки процессов использует этот интерфейс, чтобы найти все контексты глобальное выражение, связанное с помощью данного потока.  
  
> [!NOTE]
> Этот интерфейс вызывается из потока интерес. Это зависит от разработчика для идентификации текущего потока и возврата соответствующего перечислителя.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IProvideExpressionContexts` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Возвращает перечислитель контекстов выражений, известных этим компонентом.|