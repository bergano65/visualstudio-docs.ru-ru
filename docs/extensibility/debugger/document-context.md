---
title: Контекст документов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738917"
---
# <a name="document-context"></a>Контекст документа
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке *контекст документа:*

- Представляет позицию в исходном файле. Для языков, в которых исходный файл может не присутствовать, контекст документа определяет позицию в документе, обычно генерируемом средой времени выполнения. Например, движок скриптов может создать документ из скрипта. Для получения дополнительной информации [см.](../../extensibility/debugger/document-position.md)

- Описывает позицию в исходном документе, соответствующем контексту кода. Обработчик символов отображает контекст кода в контексте документации, используя информацию, генерируемую компилятором или переводчиком.

- Реализован интерфейсом [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>См. также
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [Поставщик символов](../../extensibility/debugger/symbol-provider.md)
- [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Контексты debugger](../../extensibility/debugger/debugger-contexts.md)
