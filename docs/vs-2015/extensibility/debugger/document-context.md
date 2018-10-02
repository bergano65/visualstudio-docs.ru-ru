---
title: Контекст документа | Документация Майкрософт
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
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a9e92976af5e098dca0d1a4bb81c777eb38a9f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563915"
---
# <a name="document-context"></a>Контекст документа
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [контекст документа](https://docs.microsoft.com/visualstudio/extensibility/debugger/document-context).  
  
В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, **контекст документа**:  
  
-   Представляет позицию в исходном файле. Для языков, где исходный файл может отсутствовать контекст документа определяет позицию, в документе, обычно создается средой выполнения. Например обработчик скриптов может создать документ из скрипта. Дополнительные сведения см. в разделе [позиции документа](../../extensibility/debugger/document-position.md).  
  
-   Описание позиции в исходном документе, соответствующий контекст кода. Обработчик символов сопоставляется контекста документации, используя данные, созданные компилятором или интерпретатором контекст кода.  
  
-   Реализуется [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [Поставщик символов](../../extensibility/debugger/symbol-provider.md)   
 [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)

