---
title: "IDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugIDECallback"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Включает средство оценки выражений \(EE\) для отображения сообщения в окне вывода отладчика.  
  
## Синтаксис  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## Примечания для разработчиков  
 Этот обратный вызов реализуется Подсистема управляемой отладки.  
  
## Примечания для вызывающих объектов  
 Он может использоваться средство оценки выражений для отправки выходных данных в окне вывода.  
  
## Методы  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[DisplayMessage](../Topic/IDebugIDECallback::DisplayMessage.md)|Отправляет заданной строкой сообщения в окне вывода.|  
  
## Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll