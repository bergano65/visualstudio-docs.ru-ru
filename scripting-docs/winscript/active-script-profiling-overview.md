---
title: Обзор профилирования активных скриптов | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b85410af965fdb9fe4785efe2cf12051e19436e
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797364"
---
# <a name="active-script-profiling-overview"></a>Обзор профилирования активных скриптов
[Интерфейсы профилировщика активных скриптов](../winscript/reference/active-script-profiler-interfaces.md) обеспечивают профилирование обработчика скриптов. Профилирование активных скриптов состоит из следующих частей:  
  
- Модуль языка  
  
- Host  
  
- Приложение  Profiler  
  
## <a name="language-engine"></a>Модуль языка  
 Модуль языка выполняет скрипт. Он предоставляет методы, обеспечивающие профилирование кода скрипта по мере его выполнения. Когда включено профилирование, модуль языка принимает в качестве аргумента идентификатор класса (CLSID) COM-объекта профилировщика. Он создает экземпляр COM-объекта профилировщика и затем вызывает профилировщик при возникновении различных событий.  
  
 Модуль языка реализует [интерфейс IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
> Языковая среда выполнения [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] проверяет переменную среды JS_PROFILER при создании, чтобы определить, нужно ли включать профилирование. Если этой переменной присвоен идентификатор CLSID профилировщика, языковая среда выполнения создает экземпляр COM-объекта профилировщика, используя значение переменной, чтобы определить, какой профилировщик создать.  
  
## <a name="host"></a>Host  
 Сервер создает модуль языка и предоставляет его вместе со скриптами, которые нужно выполнить. Интеллектуальный сервер также предоставляет контекст документа, который может использоваться отладчиком или профилировщиком для предоставления более подробных данных при отладке или профилировании.  
  
## <a name="profiler"></a>Приложение  Profiler  
 Профилировщик получает вызовы из модуля языка при возникновении различных событий. Профилировщик должен быть зарегистрирован как COM-объект и должен реализовывать [интерфейс IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы профилировщика активных скриптов](../winscript/reference/active-script-profiler-interfaces.md)