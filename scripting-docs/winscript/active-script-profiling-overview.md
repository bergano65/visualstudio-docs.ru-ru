---
title: Обзор профилирования активных скриптов | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5313bad4b1145216d6e04607242ed1ca131694
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835723"
---
# <a name="active-script-profiling-overview"></a>Обзор профилирования активных скриптов
[Интерфейсы профилировщика активных скриптов](../winscript/reference/active-script-profiler-interfaces.md) обеспечивают профилирование обработчика скриптов. Профилирование активных скриптов состоит из следующих частей:  
  
- модуль языка;  
  
- Узел  
  
- Profiler  
  
## <a name="language-engine"></a>модуль языка;  
 Модуль языка выполняет скрипт. Он предоставляет методы, обеспечивающие профилирование кода скрипта по мере его выполнения. Когда включено профилирование, модуль языка принимает в качестве аргумента идентификатор класса (CLSID) COM-объекта профилировщика. Он создает экземпляр COM-объекта профилировщика и затем вызывает профилировщик при возникновении различных событий.  
  
 Модуль языка реализует [интерфейс IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
> Языковая среда выполнения [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] проверяет переменную среды JS_PROFILER при создании, чтобы определить, нужно ли включать профилирование. Если этой переменной присвоен идентификатор CLSID профилировщика, языковая среда выполнения создает экземпляр COM-объекта профилировщика, используя значение переменной, чтобы определить, какой профилировщик создать.  
  
## <a name="host"></a>Узел  
 Сервер создает модуль языка и предоставляет его вместе со скриптами, которые нужно выполнить. Интеллектуальный сервер также предоставляет контекст документа, который может использоваться отладчиком или профилировщиком для предоставления более подробных данных при отладке или профилировании.  
  
## <a name="profiler"></a>Profiler  
 Профилировщик получает вызовы из модуля языка при возникновении различных событий. Профилировщик должен быть зарегистрирован как COM-объект и должен реализовывать [интерфейс IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Дополнительно  
 [Интерфейсы профилировщика активных скриптов](../winscript/reference/active-script-profiler-interfaces.md)