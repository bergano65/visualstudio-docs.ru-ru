---
title: Включение программы для отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993182"
---
# <a name="enabling-a-program-to-be-debugged"></a>Включение программы для отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Прежде, чем ваш модуль отладки (DE) можно отлаживать программы, необходимо сначала запустить DE или присоединить ее к существующей программы.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение порта](../../extensibility/debugger/getting-a-port.md)  
 В этой статье описывается получение порта на первом этапе, чтобы Включение программы для отладки.  
  
 [Регистрация программы](../../extensibility/debugger/registering-the-program.md)  
 Объясняет, следующим шагом Включение программы для отладки: регистрировать его через порт. После регистрации можно отлаживать программы, процесс присоединения или отладки just-in-time (JIT).  
  
 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md)  
 Объясняет, следующий шаг: чтобы подключить отладчик к программе.  
  
 [Присоединение основе запуска](../../extensibility/debugger/launch-based-attachment.md)  
 Описывает вложение на основе запуска для программы, которое выполняется автоматически при запуске, SDM.  
  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)  
 Шаги по требуемых событий при создании модуля отладки (DE) и подключите его к программе.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Определяет модуля отладки (DE) и описание служб, реализуемых через интерфейсы DE и как они могут вызвать отладчик для перехода между различные рабочие режимы.
