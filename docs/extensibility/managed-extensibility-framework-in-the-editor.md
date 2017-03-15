---
title: "Managed Extensibility Framework в редакторе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework в редакторе
Редактор построен с помощью компонентов Managed Extensibility Framework (MEF). Можно создавать собственные компоненты MEF расширить редактор и коде можно использовать редактор компонентов, а также.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Общие сведения о Managed Extensibility Framework  
 MEF — это библиотека .NET, которая позволяет добавлять и изменять компоненты приложения или компонента, который соответствует модели программирования MEF. Редактор Visual Studio можно указать и использовать компоненты MEF.  
  
 MEF содержится в сборке .NET Framework версии 4 System.ComponentModel.Composition.dll.  
  
 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Компоненты и контейнеры композиции  
 В компоненте — это класс или член класса, который может выполнять одно (или оба) из следующих:  
  
-   Использование другого компонента.  
  
-   Используемый другим компонентом  
  
 Например рассмотрим приложение покупок, имеющее запись заказа, зависящий от предоставляемых компонента инвентаризации хранилища данных о доступности продукта. В терминах MEF, часть инвентаризации можно *Экспорт* данные о доступности продукта и запись часть заказ может *импорта* данных. Запись заказа и части инвентаризации не нужно знать друг о друге; *контейнер композиции* (предоставляемое ведущего приложения) отвечает за обслуживание набору экспортов и разрешении экспорты и импортирует.  
  
 Контейнер композиции <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, обычно владельцем узла.</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> Контейнер композиции поддерживает *каталога* экспортированный составных частей.  
  
### <a name="exporting-and-importing-component-parts"></a>Экспорт и импорт компонентов  
 Можно экспортировать любые функции, при условии, что он реализуется как открытый класс или открытый член класса (свойство или метод). Необходимо унаследовать вашего компонента <xref:System.ComponentModel.Composition.Primitives.ComposablePart>.</xref:System.ComponentModel.Composition.Primitives.ComposablePart> Вместо этого необходимо добавить <xref:System.ComponentModel.Composition.ExportAttribute>атрибута к классу или члену класса, который требуется экспортировать.</xref:System.ComponentModel.Composition.ExportAttribute> Этот атрибут задает *контракта* какие другим компонентом часть можно импортировать ваших функциональных возможностей.  
  
### <a name="the-export-contract"></a>Контракт экспорта  
 <xref:System.ComponentModel.Composition.ExportAttribute>Определяет сущность (класс, интерфейс или структура), экспортируемой.</xref:System.ComponentModel.Composition.ExportAttribute> Как правило атрибут export принимает параметр, указывающий тип экспорта.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 По умолчанию <xref:System.ComponentModel.Composition.ExportAttribute>атрибут определяет контракт, является типом класса экспорт.</xref:System.ComponentModel.Composition.ExportAttribute>  
  
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
  
### <a name="importing-a-mef-export"></a>Импорт, экспорт MEF  
 Если вы хотите использовать экспорт MEF, необходимо знать контракта (обычно тип), в котором он был экспортирован и добавьте <xref:System.ComponentModel.Composition.ImportAttribute>, что значения атрибута.</xref:System.ComponentModel.Composition.ImportAttribute> По умолчанию атрибут импорта принимает один параметр, который является типом класса, который он модифицирует. Следующие строки кода импорта <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>тип.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Получение функциональные возможности редактора из части компонентов MEF  
 Если существующий код входит в состав компонентов MEF, можно использовать метаданные MEF для использования редактора компонентов.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Чтобы использовать функциональные возможности редактора в компоненте MEF  
  
1.  Добавление ссылки на System.Composition.ComponentModel.dll, который находится в глобальный кэш сборок (GAC), и редактор сборки.  
  
2.  Добавьте соответствующие операторы using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Добавление `[Import]` атрибута к интерфейсу службы следующим образом.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  При оформлении службы можно использовать один из его компонентов.  
  
5.  При компиляции сборки, поместите его в... \Common7\IDE\Components\ папка установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Служба языка и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
