---
title: Контекст оценки выражения (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738736"
---
# <a name="expression-evaluation-context"></a>Контекст оценки выражения
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке **контекст оценки выражения:**

- Представляет контекст для оценки выражения. Как правило, контекст оценки соответствует лексической области, в рамках которой для оценки переменных, параметров, функций и методов. Например, контекст оценки выражения, связанный с кадром стека, будет предоставлять контекст для оценки локальных переменных, параметров метода и членов класса (если это применимо).

- Существует, когда программа остановилась в точке разрыва. Само выражение представляет собой структуру данных, представляющую разогнанные выражения, готовые к связыванию и оценке в данном контексте.

     Более подробно выражения создаются с помощью метода [ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) При оценке выражения создается строка, содержащая имя и тип переменной или аргумента и ее значение. Эта строка отображается в окне Смотреть или в окне Местных жителей IDE.

     `BSTR` Учитывая интерфейс [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) отладка двигателя (DE) может создать интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) путем разбора выражения. Учитывая `IDebugExpression2` интерфейс, DE может получить значение через синхронную или асинхронную оценку выражения. Это значение, наряду с именем и типом переменной или аргументом, отправляется в IDE для отображения.

## <a name="see-also"></a>См. также
- [Интерфейсы оценки экспрессии](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Контексты debugger](../../extensibility/debugger/debugger-contexts.md)
