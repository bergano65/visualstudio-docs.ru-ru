---
title: Вложение на основе запуска | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e52e364e49bb38e6be812edec9f5fa5d8f26df0f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561374"
---
# <a name="launch-based-attachment"></a>Вложение на основе запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вложение на основе запуска](https://docs.microsoft.com/visualstudio/extensibility/debugger/launch-based-attachment).  
  
Вложение на основе запуска программы выполняется автоматически. При запуске процесса, размещающего программы, SDM вложение на основе запуска следует путь, у метода вручную вложения. Сведения см. в разделе [присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Присоединение процесса  
 Основное различие заключается в последовательность событий следующие **Attach** вызвать, как показано ниже:  
  
1.  Отправить **IDebugEngineCreateEvent2** объект события для SDM. Дополнительные сведения см. в разделе [отправки событий](../../extensibility/debugger/sending-events.md).  
  
2.  Вызовите `IDebugProgram2::GetProgramId` метод **IDebugProgram2** передается интерфейс **Attach** метод.  
  
3.  Отправить **IDebugProgramCreateEvent2** объект события для уведомления SDM, локальной **IDebugProgram2** объект был создан для представления программы для DE.  
  
4.  Отправить [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) объект события для уведомления SDM о том, что для процесса, запустившего создается новый поток.  
  
## <a name="see-also"></a>См. также  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

