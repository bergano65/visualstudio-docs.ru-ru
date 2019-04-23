---
title: Managed Extensibility Framework в редакторе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 708d9c7e41a3be24f9eaf28d86da94d47b187a93
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054018"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework в редакторе
Редактор создается с помощью компонентов Managed Extensibility Framework (MEF). Можно создавать собственные компоненты MEF для расширения редактора, а ваш код может использовать редактор компонентов, а также.

## <a name="overview-of-the-managed-extensibility-framework"></a>Общие сведения о Managed Extensibility Framework
 MEF — это библиотека .NET, которая позволяет добавлять и изменять компоненты приложения или компонента, который соответствует модели программирования MEF. В редакторе Visual Studio могут предоставить и использовать компоненты MEF.

 MEF, содержащийся в .NET Framework версии 4 *System.ComponentModel.Composition.dll* сборки.

 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Компоненты и контейнеры композиций
 В компоненте — это класс или член класса, который можно выполнить один (или оба) из следующих:

- Использовать другой компонент

- Быть использованы другим компонентом

  Например рассмотрим приложение о покупках, имеющий запись заказа, зависит от доступности данных продукта, предоставленное компонентом инвентаризации хранилища. В терминах MEF, часть инвентаризации можно *Экспорт* данные о доступности продукта и может часть запись заказа *импорта* данные. Ввода в порядке, а часть инвентаризации не нужно знать друг о друге; *контейнер композиции* (предоставляемое ведущего приложения) отвечает за обслуживание набор экспортов и разрешении экспорты и импортирует.

  Контейнер композиции, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, обычно принадлежит узел. Хранит контейнер композиции *каталога* экспортированного составных частей.

### <a name="export-and-import-component-parts"></a>Экспорт и импорт компонентов
 Вы можете экспортировать любые функции, до тех пор, пока она реализуется как открытый класс или открытый член класса (свойство или метод). У вас для получения вашего компонента из <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Вместо этого необходимо добавить <xref:System.ComponentModel.Composition.ExportAttribute> атрибут к классу или член класса, который вы хотите экспортировать. Этот атрибут указывает *контракта* какие другим компонентом часть можно импортировать функциональные возможности по работе.

### <a name="the-export-contract"></a>Экспорт контракта
 <xref:System.ComponentModel.Composition.ExportAttribute> Определяет сущность (класс, интерфейс или структура), который выполняется экспорт. Как правило атрибут export принимает параметр, указывающий тип экспорта.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 По умолчанию <xref:System.ComponentModel.Composition.ExportAttribute> атрибута определяет контракт, который является типом класса экспорт.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 В примере, значение по умолчанию `[Export]` атрибут эквивалентен `[Export(typeof(TestAdornmentLayerDefinition))]`.

 Можно также экспортировать свойства или метода, как показано в следующем примере.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Импорт и экспорт MEF
 Если вы хотите использовать экспорт MEF, необходимо знать контракта (обычно тип), по которому он был экспортирован и добавьте <xref:System.ComponentModel.Composition.ImportAttribute> атрибут, имеющий это значение. По умолчанию атрибут import принимает один параметр, который является типом класса, который изменяет его. В следующих строках кода импорта <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> типа.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Получение функциональных из части компонентов MEF
 Если существующий код входит в состав компонентов MEF, можно использовать MEF-метаданных для использования редактора компонентов.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Для использования функциональных от части компонентов MEF

1. Добавьте ссылки на *System.Composition.ComponentModel.dll*, в глобальный кэш сборок (GAC), и к сборкам редактора.

2. Добавьте соответствующую операторы using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Добавление `[Import]` атрибут интерфейсу службы, следующим образом.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Когда вы получили службу, вы можете использовать один из его компонентов.

5. При компиляции сборки, поместите его *... \Common7\IDE\Components\* папке установки Visual Studio.

## <a name="see-also"></a>См. также
- [Точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)