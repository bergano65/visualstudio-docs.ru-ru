---
title: "Особые свойства ошибок из асинхронных методов среды выполнения Windows | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Специальные свойства ошибок из асинхронных методов среды выполнения Windows
Отладка асинхронных методов среды выполнения Windows на яызке JavaScript может представлять трудности, так как ошибка может возникать глубоко в стеке вызовов. Объект JavaScript `Error` имеет дополнительные свойства, которые появляются только при возникновении ошибки в асинхронном методе среды выполнения Windows, когда приложение выполняется в режиме отладки.  
  
## <a name="special-error-properties"></a>Особые свойства ошибок  
 Объект ошибки, который формируется в результате ошибки в асинхронной операции среды выполнения Windows в режиме отладки, имеет следующие особые свойства:  
  
-   `asyncOpSource` (объект) — получает сведения об исходном расположении, где был выполнен вызов, который привел к ошибке. Свойство `asyncOpSource.originatingCall` (строка) отображает место в пользовательском коде, где начала выполняться асинхронная операция.  
  
-   asyncOpType (строка) — возвращает имя типа асинхронной операции, которая привела к ошибке.  
  
 Дополнительные сведения об ошибках в асинхронных операциях см. в разделах:  
  
-   [Как обрабатывать ошибки с объектами Promise](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Диагностика ошибок среды выполнения Windows](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)