---
title: Вложение на основе запуска | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 1c3d361d9e8b99467e0a8a131e9d30be5db30b9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792454"
---
# <a name="launch-based-attachment"></a>Вложение на основе запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

