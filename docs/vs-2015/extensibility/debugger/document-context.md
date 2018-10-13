---
title: Контекст документа | Документация Майкрософт
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
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e1bbe5ac2f2c752fcf6f0b5a0b0b95be144ac8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237436"
---
# <a name="document-context"></a>Контекст документа
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, **контекст документа**:  
  
-   Представляет позицию в исходном файле. Для языков, где исходный файл может отсутствовать контекст документа определяет позицию, в документе, обычно создается средой выполнения. Например обработчик скриптов может создать документ из скрипта. Дополнительные сведения см. в разделе [позиции документа](../../extensibility/debugger/document-position.md).  
  
-   Описание позиции в исходном документе, соответствующий контекст кода. Обработчик символов сопоставляется контекста документации, используя данные, созданные компилятором или интерпретатором контекст кода.  
  
-   Реализуется [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [Поставщик символов](../../extensibility/debugger/symbol-provider.md)   
 [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)

