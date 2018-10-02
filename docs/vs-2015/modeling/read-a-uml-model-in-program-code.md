---
title: Чтение модели UML в программном коде | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: f55126366fc80830edd92b16d64c51991c13e731
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560029"
---
# <a name="read-a-uml-model-in-program-code"></a>Чтение модели UML в программном коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [чтение модели UML в программном коде](https://docs.microsoft.com/visualstudio/modeling/read-a-uml-model-in-program-code).  
  
Вы можете загрузить модель UML и ее схемы, используя UML API.  
  
##  <a name="Reading"></a> Чтение модели в программном коде  
 Чтобы получить доступ к содержимому модели, не отображая ее в окне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], используйте метод `ModelingProject.LoadReadOnly()`.  
  
 Например:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 Если нужно прочитать фигуры на схеме, необходимо сначала прочитать проект, а затем схему.  
  
 Например:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>Альтернативные методы  
 Для многих приложений [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus позволяет ссылаться на модели и элементы внутри них, обеспечивая большую надежность и гибкость, чем с помощью методов, описанных в этом разделе. Она предоставляет стандартный метод создания ссылок между произвольными элементами в одной модели или разных моделях. Дополнительные сведения см. в разделе [интеграция моделей UML с другими моделями и средствами](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Кроме того, с помощью API-интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно открывать модели и схемы в пользовательском интерфейсе. Дополнительные сведения см. в разделе [Открытие модели UML с помощью Visual Studio API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
##  <a name="Standalone"></a> Автономные приложения  
 Пример из предыдущего подраздела можно выполнить в расширениях Visual Studio. Можно прочитать модель в отдельном приложении, однако необходимо добавить несколько ссылок на проект [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  Вероятно, способы прочтения модели в отдельном приложении будут изменены в последующих выпусках продукта. Некоторые функции, доступные в текущей версии, могут оказаться недоступными в последующих выпусках.  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Добавление ссылок для чтения модели в отдельном приложении  
  
1.  В обозревателе решений щелкните правой кнопкой мыши проект, в котором выполняется сборка приложения и нажмите кнопку **свойства**. В редакторе свойств в **приложения** вкладке **требуемой версии .NET Framework** до требуемой версии платформы .NET Framework.  
  
2.  Добавьте ссылки [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)], необходимые для доступа к моделям UML, например:  
  
    -   Microsoft.VisualStudio.Uml.Interfaces.dll  
  
    -   Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3.  Помимо ссылок, перечисленных в предыдущих разделах, добавьте в проект следующие ссылки из **\Common7\IDE\PrivateAssemblies Visual Studio [версия] \Program Files\Microsoft**:  
  
    -   Microsoft.VisualStudio.Uml.dll  
  
    -   Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     Если нужно обеспечить возможность чтения схем в приложении, потребуются также следующие ссылки:  
  
    -   Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
    -   Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
    -   Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
    -   Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
    -   Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>См. также  
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)   
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)



