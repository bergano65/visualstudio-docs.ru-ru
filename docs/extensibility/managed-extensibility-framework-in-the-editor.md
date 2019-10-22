---
title: Managed Extensibility Framework в редакторе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f376a43b6d59ba494db2ad4e5ef26b260d91f6ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632612"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework в редакторе
Редактор строится с помощью компонентов Managed Extensibility Framework (MEF). Вы можете создавать собственные компоненты MEF для расширения редактора, а код может также использовать компоненты редактора.

## <a name="overview-of-the-managed-extensibility-framework"></a>Общие сведения о Managed Extensibility Framework
 MEF — это библиотека .NET, которая позволяет добавлять и изменять компоненты приложения или компонента, которые следуют за моделью программирования MEF. Редактор Visual Studio может предоставлять и использовать компоненты MEF.

 MEF содержится в сборке .NET Framework версии 4 *System. ComponentModel. композиция. dll* .

 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Части компонентов и контейнеры композиции
 Часть компонента — это класс или член класса, который может выполнять одно (или оба) из следующих действий:

- Использование другого компонента

- Использовать другим компонентом

  Например, рассмотрим приложение для покупок, которое имеет компонент записи заказа, зависящий от данных о доступности продукта, предоставляемых компонентом складских запасов. В терминах MEF компонент инвентаризации может *экспортировать* данные о доступности продуктов, а часть заказа может *импортировать* данные. Часть записи заказа и часть инвентаризации не должны быть осведомлены о них. *контейнер композиции* (предоставляемый ведущим приложением) отвечает за поддержание набора экспортов и разрешение экспорта и импорта.

  Контейнер композиции, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, обычно принадлежит узлу. Контейнер композиции хранит *Каталог* экспортированных частей компонентов.

### <a name="export-and-import-component-parts"></a>Экспорт и импорт частей компонентов
 Можно экспортировать любую функциональность, если она реализована как открытый класс или открытый член класса (свойство или метод). Не требуется создавать часть компонента из <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Вместо этого необходимо добавить атрибут <xref:System.ComponentModel.Composition.ExportAttribute> в класс или член класса, который требуется экспортировать. Этот атрибут указывает *контракт* , по которому другая часть компонента может импортировать ваши функции.

### <a name="the-export-contract"></a>Экспортный контракт
 @No__t_0 определяет экспортируемый объект (класс, интерфейс или структура). Как правило, атрибут Export принимает параметр, указывающий тип экспорта.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 По умолчанию атрибут <xref:System.ComponentModel.Composition.ExportAttribute> определяет контракт, который является типом экспортируемого класса.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 В этом примере атрибут `[Export]` по умолчанию эквивалентен `[Export(typeof(TestAdornmentLayerDefinition))]`.

 Можно также экспортировать свойство или метод, как показано в следующем примере.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Импорт экспорта MEF
 Если требуется использовать экспорт MEF, необходимо получить сведения о контракте (обычно это тип), по которому он был экспортирован, и добавить атрибут <xref:System.ComponentModel.Composition.ImportAttribute>, имеющий это значение. По умолчанию атрибут import принимает один параметр, который является типом класса, который он изменяет. Следующие строки кода импортируют тип <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Получение функциональных возможностей редактора из части компонента MEF
 Если существующий код является частью компонента MEF, можно использовать метаданные MEF для использования частей компонента редактора.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Использование функциональных возможностей редактора из части компонента MEF

1. Добавьте ссылки на *System. композиция. ComponentModel. dll*, который находится в глобальном кэше сборок (GAC), и в сборки редактора.

2. Добавьте соответствующие директивы using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Добавьте атрибут `[Import]` в интерфейс службы, как показано ниже.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. После получения службы можно использовать любой из ее компонентов.

5. После компиляции сборки вставьте ее в *.. \Common7\IDE\Components \* папка установки Visual Studio.

## <a name="see-also"></a>См. также
- [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)
