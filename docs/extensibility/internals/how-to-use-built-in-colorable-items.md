---
title: 'Как: использовать встроенные цветные элементы | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6cf51516677aeca71dba269bcdd132e0830b6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129687"
---
# <a name="how-to-use-built-in-colorable-items"></a>Как: использовать встроенные цветных элементов
Прежде чем использовать встроенные цветные элементы, необходимо сначала сигнал для интегрированной среды разработки (IDE) не предоставляется собственные пользовательские цветных элементов, которые, в этом случае <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> объектов. Это можно сделать, задав запись реестра для языковой службы.  
  
### <a name="to-use-built-in-colorable-items"></a>Чтобы использовать встроенные цветных элементов  
  
1.  В разделе HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*службы \Languages\Language\\*название языка*, где *X.Y* — это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и *название языка* имя языка, создать значение записи реестра типа DWORD `RequestStockColors`.  
  
2.  Задать `RequestStockColors` значение записи реестра на 1.  
  
     После создания запись реестра, ваш colorizer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> члены можно использовать метод <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> перечисления для заполнения массива атрибутов цвета для использования в редакторе.  
  
    > [!NOTE]
    >  Не устанавливайте этот параметр реестра, если предоставляется пользовательский цветных элементов. Дополнительные сведения см. в разделе [цветные элементы пользовательских](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>См. также  
 [Синтаксис, выделение цветом в редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Синтаксиса в языковую службу прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация Цветовая подсветка синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Цветные настраиваемые элементы](../../extensibility/internals/custom-colorable-items.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)