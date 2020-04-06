---
title: 'Как: Используйте встроенные цветные предметы Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707791"
---
# <a name="how-to-use-built-in-colorable-items"></a>Как: Использование встроенных цветных элементов
Прежде чем использовать встроенные цветные элементы, необходимо сначала подать сигнал интегрированной среде разработки (IDE), что вы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> не предоставляете свои собственные собственные цветные элементы, которые в этом случае будут объектами. Вы делаете это, устанавливая запись в реестре для языковой службы.

## <a name="to-use-built-in-colorable-items"></a>Использовать встроенные цветные элементы

1. Под **HKEY_LOCAL_MACHINE-VisualStudio\\<X.Y>\\ языковых\>услуг<языковое имя**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<где \<X.Y> является версия и имя языка> имя вашего языка, создать DWORD регистрации значение под названием **RequestStockColors**.

2. Установите значение входа в реестр **RequestStockColors** до *1*.

    После создания записи в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> реестре метод раскрашивания <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> может использовать участники перечисления для заполнения массива цветовых атрибутов для использования редактором.

   > [!NOTE]
   > Не устанавливайте эту запись реестра, если вы предоставляете пользовательские цветные элементы. Для получения дополнительной [информации см.](../../extensibility/internals/custom-colorable-items.md)

## <a name="see-also"></a>См. также
- [Синтаксис раскраски в пользовательских редакторов](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Раскраска Syntax в устаревшей языковой службе](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация окраски синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)
- [Пользовательские цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service2.md)
