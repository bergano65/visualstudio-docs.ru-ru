---
title: Рамочная программа управляемого расширяемости в редакторе Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702866"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Рамочная система управляемой расширительности в редакторе
Редактор построен с использованием компонентов управляемой расширительности (MEF). Вы можете создать свои собственные компоненты MEF для расширения редактора, и ваш код может использовать компоненты редактора, а также.

## <a name="overview-of-the-managed-extensibility-framework"></a>Обзор Рамочной системы управляемого расширяемости
 MEF — это библиотека .NET, которая позволяет добавлять и изменять функции приложения или компонента, следующего за моделью программирования MEF. Редактор Visual Studio может как предоставлять, так и потреблять компоненты MEF.

 MEF содержится в версии .NET Framework 4 *System.ComponentModel.Composition.dll* сборки.

 Для получения дополнительной информации о MEF [см.](/dotnet/framework/mef/index)

### <a name="component-parts-and-composition-containers"></a>Компонентные детали и контейнеры для композиций
 Компонентной частью является класс или член класса, который может сделать один (или оба) из следующих:

- Потребляйте другой компонент

- Потреблено другим компонентом

  Например, рассмотрим приложение для покупок с компонентом ввода заказа, который зависит от данных о наличии продукта, предоставленных компонентом складских запасов. С точки зрения MEF, инвентарная часть может *экспортировать* данные о доступности продукта, а часть ввода заказа может *импортировать* данные. Часть входа заказа и инвентарная часть не должны знать друг о друге; *контейнер состава* (предоставленный принимающей заявкой) отвечает за поддержание набора экспорта и решение вопросов экспорта и импорта.

  Контейнер композиции, как правило, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>принадлежит хостам. Контейнер состава ведет *каталог* экспортированных компонентов.

### <a name="export-and-import-component-parts"></a>Экспортные и импортные компоненты
 Вы можете экспортировать любую функциональность, если она реализована в качестве общедоступного класса или публичного члена класса (свойства или метода). Вам не нужно получать компонентную <xref:System.ComponentModel.Composition.Primitives.ComposablePart>часть из. Вместо этого необходимо <xref:System.ComponentModel.Composition.ExportAttribute> добавить атрибут в класс или член класса, который вы хотите экспортировать. Этот атрибут определяет *контракт,* по которому другая часть компонента может импортировать вашу функциональность.

### <a name="the-export-contract"></a>Экспортный контракт
 Определяет <xref:System.ComponentModel.Composition.ExportAttribute> объект (класс, интерфейс или структуру), который экспортируется. Как правило, экспортный атрибут принимает параметр, который определяет тип экспорта.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 По умолчанию <xref:System.ComponentModel.Composition.ExportAttribute> атрибут определяет контракт, который является типом класса экспорта.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 В этом примере `[Export]` атрибут по `[Export(typeof(TestAdornmentLayerDefinition))]`умолчанию эквивалентен .

 Вы также можете экспортировать свойство или метод, как показано в следующем примере.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Импорт экспорта MEF
 Если вы хотите потреблять экспорт MEF, вы должны знать контракт (обычно тип), по <xref:System.ComponentModel.Composition.ImportAttribute> которому он был экспортирован, и добавить атрибут, который имеет это значение. По умолчанию атрибут импорта принимает один параметр, который является типом класса, который он изменяет. Следующие строки кода <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> импортируют тип.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Получите функциональность редактора из компонентной части MEF
 Если существующий код является составной частью MEF, вы можете использовать метаданные MEF для потребления компонентов редактора.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Потребление функциональности редактора из компонентной части MEF

1. Добавить ссылки на *System.Composition.ComponentModel.dll*, который находится в глобальной сборки кэша (GAC), и в сборки редактора.

2. Добавьте соответствующие директивы.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Добавьте `[Import]` атрибут в интерфейс службы следующим образом.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Получив услугу, можно использовать любой из ее компонентов.

5. Когда вы составили сборку, поместите ее в к.. Папка компонентов\* установки Visual Studio.

## <a name="see-also"></a>См. также
- [Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
