---
title: "Интерфейс IProvideExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts — интерфейс"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IProvideExpressionContexts
Предоставляет способ перечисления контекстах выражения известные некоторым компонентом.  Обработчики скриптов, как правило, реализуют данный интерфейс.  
  
 Процесс отладки использования диспетчера этот интерфейс найти все глобальные контекстах выражения, ассоциированные с данным потоком.  
  
> [!NOTE]
>  Этот интерфейс вызвать из потока.  Он принимает разработчик, чтобы определить текущий поток и вернуть соответствующий перечислитель.  
  
## Методы  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IProvideExpressionContexts` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Возвращает перечислитель для контекстов выражения известных этим компонентом.|