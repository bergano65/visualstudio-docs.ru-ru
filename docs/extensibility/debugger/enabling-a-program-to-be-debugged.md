---
title: "Включение отлаживаемой программы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 66daff038c7556a693964d5dabc4de054990d791
ms.lasthandoff: 02/22/2017

---
# <a name="enabling-a-program-to-be-debugged"></a>Включение программы для отладки
Перед своим отладчиком (DE) можно отлаживать программы, необходимо запустить DE или присоединить ее к существующей программы.  
  
## <a name="in-this-section"></a>Содержание  
 [Приступая к порту](../../extensibility/debugger/getting-a-port.md)  
 Описывает получение порт на первом этапе Включение отлаживаемой программы.  
  
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)  
 Объясняет следующий шаг в обеспечении отлаживаемой программы: его регистрации с портом. После регистрации можно отлаживать программы либо в процессе присоединения или отладки just-in-time (JIT).  
  
 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md)  
 Объясняет следующий шаг: присоединить отладчик к программе.  
  
 [Подключение на основе запуска](../../extensibility/debugger/launch-based-attachment.md)  
 Описание вложения на основе запуска программы, которая выполняется автоматически при запуске, SDM.  
  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)  
 Этапы необходимые события при создании модуля отладки (DE) и подключение к программе.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательские отладки ядра](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Определяет отладчик (DE) и описание служб, реализуется с помощью интерфейсов DE и как они могут вызвать отладчик для перехода между различными режимами рабочей.
