---
title: Как использовать встроенные цветные элементы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842477"
---
# <a name="how-to-use-built-in-colorable-items"></a>Практическое руководство. Использование встроенных цветных элементов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Перед использованием встроенных цветовых элементов необходимо сначала сообщить в интегрированную среду разработки (IDE), которая не предоставляет собственные настраиваемые цветовые элементы, которые в данном случае будут <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> объектами. Это делается путем настройки записи реестра для языковой службы.  
  
### <a name="to-use-built-in-colorable-items"></a>Использование встроенных цветовых элементов  
  
1. В разделе HKEY_LOCAL_MACHINE \Висуалстудио \\ *X. y*\Лангуажес\лангуаже Services \\ *Language Name*, где *X. y* — версия [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и *название языка* — это имя вашего языка, создайте значение записи реестра типа DWORD с именем `RequestStockColors` .  
  
2. Присвойте параметру `RequestStockColors` реестра значение 1.  
  
     После создания записи в реестре метод, используемый в этом <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> перечислении, может использовать члены <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> перечисления для заполнения массива атрибутов цвета, используемых редактором.  
  
    > [!NOTE]
    > Не устанавливайте эту запись реестра, если вы предоставляете настраиваемые цветные элементы. Дополнительные сведения см. в разделе [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>См. также:  
 [Выделение синтаксиса в пользовательских редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Выделение синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация цветового выделения синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)
