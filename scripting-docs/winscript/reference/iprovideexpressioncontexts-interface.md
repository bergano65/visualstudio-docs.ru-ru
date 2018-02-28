---
title: "Интерфейс IProvideExpressionContexts | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontexts-interface"></a>Интерфейс IProvideExpressionContexts
Предоставляет способ для перечисления контекстами выражения известен, определенных компонентом. Обработчики скриптов обычно реализуют этот интерфейс.  
  
 Диспетчер отладки процессов использует этот интерфейс для поиска всех глобальных выражениях контекстов, связанные с данного потока.  
  
> [!NOTE]
>  Этот интерфейс вызывается из потока, представляющие интерес. Он определяется разработчиком для идентификации текущего потока и возврата соответствующим перечислителем.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IProvideExpressionContexts` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Возвращает перечислитель контекстами выражения известен этого компонента.|