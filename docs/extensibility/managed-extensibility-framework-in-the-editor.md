---
title: "Managed Extensibility Framework в редакторе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c13b1a4e1b183b3a6f4b54f58cca3593ce5c7bb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework в редакторе
Редактор построен с помощью компоненты Managed Extensibility Framework (MEF). Можно создавать свои собственные компоненты MEF для расширения редактора, и ваш код может принимать редактора компонентов, а также.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Общие сведения о Managed Extensibility Framework  
 MEF — это библиотека .NET, которая позволяет добавлять и изменять компоненты приложения или компонента, который соответствует модели программирования MEF. В редакторе Visual Studio можно предоставить и использовать компонентов MEF.  
  
 Содержится в сборке .NET Framework версии 4 System.ComponentModel.Composition.dll MEF.  
  
 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Компоненты и контейнерах композиции  
 Компонент — это класс или член класса, который может выполнять одно (или оба) из следующих:  
  
-   Использовать другой компонент  
  
-   Быть использованы другим компонентом  
  
 Например рассмотрим приложение покупок, имеющее запись заказа, зависит от доступности данных продукта, предоставленное компонентом запасов склада. В терминах MEF часть инвентаризации можно *Экспорт* продукта доступности данных и запись часть заказ может *импорта* данных. Запись заказа и части инвентаризации не нужно знать о друг с другом; *контейнер композиции* (предоставляемое ведущего приложения) отвечает за поддержание набору экспортов и разрешении экспорты и импорта.  
  
 Контейнер композиции <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, обычно принадлежит узел. Обеспечивает контейнер композиции *каталога* экспортированного составных частей.  
  
### <a name="exporting-and-importing-component-parts"></a>Экспорт и импорт компонентов  
 Можно экспортировать любые функции, при условии, что оно реализовано как открытый класс или открытый член класса (свойство или метод). Нет необходимости наследовать вашего компонента из <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Вместо этого необходимо добавить <xref:System.ComponentModel.Composition.ExportAttribute> класс или член класса, который требуется экспортировать. Этот атрибут задает *контракта* другим компонентом какие части можно импортировать функциональные возможности по работе.  
  
### <a name="the-export-contract"></a>Экспорт контракта  
 <xref:System.ComponentModel.Composition.ExportAttribute> Определяет сущность (класс, интерфейс или структура), выполняется экспорт. Как правило атрибут export принимает параметр, указывающий тип экспорта.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 По умолчанию <xref:System.ComponentModel.Composition.ExportAttribute> атрибута определяет контракт, который является типом класса, экспорт.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 В примере, значение по умолчанию `[Export]` атрибута эквивалентно `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Можно также экспортировать свойства или метода, как показано в следующем примере.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Импорт экспорта MEF  
 Если вы хотите использовать экспорта MEF, необходимо знать контракта (обычно тип), с помощью которого он был экспортирован и добавить <xref:System.ComponentModel.Composition.ImportAttribute> атрибут, имеющий значения. По умолчанию атрибут импорта принимает один параметр, который является типом класса, который он модифицирует. В следующих строках кода импорта <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> типа.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Получение из компонент MEF функциональные возможности редактора  
 Если существующий код является частью компонента MEF, можно использовать для использования редактора компонентов MEF-метаданных.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Чтобы использовать функциональные возможности редактора в компоненте MEF  
  
1.  Добавьте ссылки на System.Composition.ComponentModel.dll, который находится в глобальный кэш сборок (GAC), и редактор сборки.  
  
2.  Добавьте соответствующую с помощью инструкций.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Добавить `[Import]` атрибута в интерфейс службы следующим образом.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  При оформлении службы можно использовать один из его компонентов.  
  
5.  При компиляции сборки, поместите его в... \Common7\IDE\Components\ папка установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)