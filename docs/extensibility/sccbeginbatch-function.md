---
title: "Функция SccBeginBatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "Функция SccBeginBatch"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccBeginBatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция запускает последовательность операций системы управления версиями пакета.[SccEndBatch](../extensibility/sccendbatch-function.md) Будет вызываться до конца пакета. Эти пакеты не могут быть вложенными.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### Параметры  
 Отсутствует.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Пакет операций успешно начата.|  
|SCC\_E\_UNKNOWNERROR|Неспецифическая ошибка.|  
  
## Заметки  
 Пакеты управления источника используются выполнять те же операции в нескольких проектов или нескольких контекстов. Пакеты можно использовать во избежание избыточных проекта диалоговых окнах работу пользователей во время пакетной операции.`SccBeginBatch` Функции и [SccEndBatch](../extensibility/sccendbatch-function.md) используются как пара функций для определения начала и окончания операции. Они не могут быть вложенными.`SccBeginBatch` Задает флаг, указывающий, что пакетная операция находится в разработке.  
  
 Когда действует пакетной операции, подключаемый модуль системы управления версиями следует не более одного диалогового окна для каких\-либо вопросов пользователь видит и применить ответ в этом диалоговом для всех последующих операций.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)