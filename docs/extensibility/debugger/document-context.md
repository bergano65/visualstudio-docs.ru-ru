---
title: Контекст документа | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dffe0c72a20acc10b45ef12068ba95015db2276f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852892"
---
# <a name="document-context"></a>Контекст документа
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, *контекст документа*:  
  
-   Представляет позицию в исходном файле. Для языков, где исходный файл может отсутствовать контекст документа определяет позицию, в документе, обычно создается средой выполнения. Например обработчик скриптов может создать документ из скрипта. Дополнительные сведения см. в разделе [позиция документа](../../extensibility/debugger/document-position.md).  
  
-   Описание позиции в исходном документе, соответствующий контекст кода. Обработчик символов сопоставляется контекста документации, используя данные, созданные компилятором или интерпретатором контекст кода.  
  
-   Реализуется [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [Поставщик символов](../../extensibility/debugger/symbol-provider.md)   
 [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)