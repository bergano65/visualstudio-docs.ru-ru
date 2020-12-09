---
title: Расположение документа | Документация Майкрософт
description: Узнайте, как расположение документа в отладке Visual Studio предоставляет абстракцию расположения в исходном файле, как известно интегрированной среде разработки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915327"
---
# <a name="document-position"></a>Расположение документа
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке, *расположение документа*:

- Предоставляет абстракцию расположения в исходном файле, как известно интегрированной среде разработки. В настоящее время для большинства языков расположение документа можно рассматривать как расположение в исходном файле.

- Описывает расположение в исходном документе для модуля отладки.

- Реализуется с помощью интерфейса [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>См. также раздел
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [Контекст документа](../../extensibility/debugger/document-context.md)
- [Поставщик символов](../../extensibility/debugger/symbol-provider.md)
- [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
