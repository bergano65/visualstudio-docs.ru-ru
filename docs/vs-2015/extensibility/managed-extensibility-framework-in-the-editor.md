---
title: Managed Extensibility Framework в редакторе | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7fb7214f4cd9d338c06e9f1eba5f1cc2c50fbc0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215674"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор создается с помощью компонентов Managed Extensibility Framework (MEF). Можно создавать собственные компоненты MEF для расширения редактора, а ваш код может использовать редактор компонентов, а также.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Общие сведения о Managed Extensibility Framework  
 MEF — это библиотека .NET, которая позволяет добавлять и изменять компоненты приложения или компонента, который соответствует модели программирования MEF. В редакторе Visual Studio могут предоставить и использовать компоненты MEF.  
  
 MEF содержится в сборке .NET Framework версии 4 System.ComponentModel.Composition.dll.  
  
 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Компоненты и контейнеры композиций  
 В компоненте — это класс или член класса, который можно выполнить один (или оба) из следующих:  
  
-   Использовать другой компонент  
  
-   Быть использованы другим компонентом  
  
 Например рассмотрим приложение о покупках, имеющий запись заказа, зависит от доступности данных продукта, предоставленное компонентом инвентаризации хранилища. В терминах MEF, часть инвентаризации можно *Экспорт* данные о доступности продукта и может часть запись заказа *импорта* данные. Ввода в порядке, а часть инвентаризации не нужно знать друг о друге; *контейнер композиции* (предоставляемое ведущего приложения) отвечает за обслуживание набор экспортов и разрешении экспорты и импортирует.  
  
 Контейнер композиции, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, обычно принадлежит узел. Хранит контейнер композиции *каталога* экспортированного составных частей.  
  
### <a name="exporting-and-importing-component-parts"></a>Экспорт и импорт частей компонента  
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
  
### <a name="importing-a-mef-export"></a>Импорт, экспорт MEF  
 Если вы хотите использовать экспорт MEF, необходимо знать контракта (обычно тип), по которому он был экспортирован и добавьте <xref:System.ComponentModel.Composition.ImportAttribute> атрибут, имеющий это значение. По умолчанию атрибут import принимает один параметр, который является типом класса, который изменяет его. В следующих строках кода импорта <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> типа.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Эффективное использование функциональных часть компонентов MEF  
 Если существующий код входит в состав компонентов MEF, можно использовать MEF-метаданных для использования редактора компонентов.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Для использования функциональных от части компонентов MEF  
  
1.  Добавьте ссылки System.Composition.ComponentModel.dll, располагающийся в глобальный кэш сборок (GAC), и редактор сборок.  
  
2.  Добавьте соответствующую операторы using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Добавление `[Import]` атрибут интерфейсу службы, следующим образом.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Когда вы получили службу, вы можете использовать один из его компонентов.  
  
5.  При компиляции сборки, поместите его... \Common7\IDE\Components\ папка установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)

