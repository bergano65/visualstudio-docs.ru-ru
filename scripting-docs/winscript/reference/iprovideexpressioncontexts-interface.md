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
ms.openlocfilehash: b40825884b3c63af6be6d8bc852a5da4805f8975
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152055"
---
# <a name="iprovideexpressioncontexts-interface"></a>Интерфейс IProvideExpressionContexts
Предоставляет способ для перечисления контекстов выражений, известных по определенному компоненту. Этот интерфейс обычно реализуется обработчиков сценариев.  
  
 Диспетчер отладки процессов использует этот интерфейс, чтобы найти все контексты глобальное выражение, связанное с помощью данного потока.  
  
> [!NOTE]
>  Этот интерфейс вызывается из потока интерес. Это зависит от разработчика для идентификации текущего потока и возврата соответствующего перечислителя.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IProvideExpressionContexts` интерфейс предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Возвращает перечислитель контекстов выражений, известных этим компонентом.|