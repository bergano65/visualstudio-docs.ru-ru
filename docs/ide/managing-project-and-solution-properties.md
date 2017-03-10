---
title: "Управление свойствами проекта и решения | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 6
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e843adb473be51e185fd3b5dc514b44f16106157
ms.lasthandoff: 02/22/2017

---
# <a name="managing-project-and-solution-properties"></a>Управление свойствами проекта и решения
У проектов есть свойства, которые определяют различные аспекты компиляции, отладки, тестирования и развертывания. Некоторые свойства являются общими для всех типов проектов, а некоторые — уникальными для конкретных языков или платформ. Чтобы получить доступ к свойствам проекта, щелкните правой кнопкой мыши узел проекта в обозревателе решений и выберите пункт "Свойства". Либо введите свойства в поле **быстрого запуска** в строке меню.  
  
 ![Контекстное меню проекта](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")  
  
 У проектов .NET также есть узел свойств в дереве проекта.  
  
 ![Узел свойств в дереве обозревателя решений](../ide/media/vs2015_props_se.png "VS2015_Props_SE")  
  
> [!TIP]
>  У решений есть несколько свойств, как и у элементов проекта. Эти свойства доступны в [окне свойств](../ide/reference/properties-window.md), а не в **конструкторе проектов**.  
  
## <a name="project-properties"></a>Свойства проекта  
 Свойства проекта упорядочены по группам, у каждой из которых есть собственная страница свойств. При этом могут использоваться различные страницы для разных языков и типов проектов.  
  
### <a name="c-and-visual-basic-projects"></a>Проекты C# и Visual Basic  
 В проектах C# и Visual Basic свойства отображаются в **конструкторе проектов**. На следующем рисунке показана страница свойств сборки для проекта WPF на C#.  
  
 ![Конструктор проектов Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")  
  
 Сведения о каждой из страниц свойств в конструкторе проектов см. в разделе [Справочник по свойствам проектов](../ide/reference/project-properties-reference.md).  
  
### <a name="c-and-javascript-projects"></a>Проекты C++ и JavaScript  
 Проекты C++ и JavaScript имеют другой пользовательский интерфейс для управления свойствами проекта. На этом рисунке показана страница свойств проекта C++ (страницы JavaScript выглядят аналогичным образом).  
  
 ![Свойства проекта Visual C++](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")  
  
 Сведения о свойствах проекта C++ см. в разделе [Работа со свойствами проектов](/visual-cpp/ide/working-with-project-properties). Дополнительные сведения о свойствах JavaScript см. в разделе [Страницы свойств (JavaScript)](../ide/reference/property-pages-javascript.md).  
  
## <a name="solution-properties"></a>Свойства решения  
 Для доступа к свойствам решения щелкните правой кнопкой мыши узел решения в **обозревателе решений** и выберите пункт **Свойства**. В открывшемся диалоговом окне можно задать параметры проекта для сборки отладки или выпуска, указать, какие проекты должны запускаться при нажатии клавиши F5, а также задать параметры анализа кода.  
  
## <a name="see-also"></a>См. также  
 [Решения и проекты в Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
