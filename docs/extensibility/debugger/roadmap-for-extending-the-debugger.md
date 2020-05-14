---
title: Дорожная карта для расширения Debugger (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713135"
---
# <a name="roadmap-for-extending-the-debugger"></a>Дорожная карта для расширения отладчика
Эта документация содержит руководство и [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] справочную информацию [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]для расширения отладчика с .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]отладка документации включает в себя образцы, всеобъемлющую ссылку и несколько репрезентативных сценариев, которые демонстрируют типичные способы настройки отладчика.

 Компилятор и его выход определяют, что необходимо для настройки отладки в продукте. Если ваш компилятор:

- Цели на нативной операционной системы Windows и пишет *. PDB* файл, вы можете отладить программы с родной код отладки двигателя (DE), который интегрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Вам не нужно реализовывать DE или оценщик амортизации. Оценщик выражения написан для синтаксиса языка программирования СЗ.

- Производит Microsoft промежуточный язык (MSIL) выход, вы можете отладить программы с управляемым кодом отладка двигателя DE, который также интегрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Таким образом, необходимо только реализовать оценщика выражения. Для вас предусмотрен оценщик выражения образца. Дополнительные сведения см. в следующих разделах:

   [Оценка экспрессии](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)

   [Контекст оценки выражения](../../extensibility/debugger/expression-evaluation-context.md)

   [Оценка выражения в режиме перерыва](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Написать общий оценщик выражения времени выполнения языка](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Цели собственной операционной системы или другой среды времени выполнения, вам нужно написать свой собственный DE. Предоставляется учебник, который создает простой DE с помощью ATL COM. Дополнительные сведения см. в следующих разделах:

   [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Учебник: Создайте отладку двигателя с помощью ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>См. также
- [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
