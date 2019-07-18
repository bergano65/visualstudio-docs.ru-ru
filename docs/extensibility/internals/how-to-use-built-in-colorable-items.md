---
title: Практическое руководство. Использование встроенных цветных элементов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae1c327c14ed2b349ee02566c5cdfd38b9a07859
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311966"
---
# <a name="how-to-use-built-in-colorable-items"></a>Практическое руководство. Использование встроенных цветных элементов
Прежде чем использовать встроенные цветные элементы, необходимо сначала сообщается в интегрированной среде разработки (IDE), вы не предоставляли собственных пользовательских цветных элементов, которые в данном случае было бы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> объектов. Для этого параметру реестра для языковой службы.

## <a name="to-use-built-in-colorable-items"></a>Чтобы использовать встроенные цветные элементы

1. В разделе **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language служб\\< название языка\>** , где \<X.Y > — это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и \<Имя_языка > — это имя языка, создайте значение записи реестра типа DWORD **RequestStockColors**.

2. Задайте **RequestStockColors** значение записи реестра для *1*.

    После создания реестра операции, ваш палитры <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод можно использовать члены <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> перечисления, заполните массив атрибутов цвета для использования с помощью редактора.

   > [!NOTE]
   > Не устанавливайте этот параметр реестра, если вы предоставляете пользовательских цветных элементов. Дополнительные сведения см. в разделе [пользовательских цветных элементов](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>См. также
- [Цветовая маркировка синтаксиса в специализированных редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Цветовая маркировка синтаксиса в языковой службы прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация цветовой маркировки синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)
- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)