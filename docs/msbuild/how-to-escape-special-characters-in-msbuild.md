---
title: "Как обеспечить пропуск специальных знаков в MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
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
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 90f2d3d94d7073d0bc694b020496996db31b342a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Как обеспечить пропуск специальных знаков в MSBuild
Некоторые символы имеют особое значение в файлах проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. К ним относятся точка с запятой (;) и звездочка (*). Полный список таких специальных знаков см. в разделе [Специальные символы в MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Чтобы использовать эти специальные знаки в качестве литералов в файле проекта, их необходимо задать с помощью синтаксиса %*xx*, где *xx* представляет шестнадцатеричное значение ASCII знака.  
  
## <a name="msbuild-special-characters"></a>Специальные символы в MSBuild  
 Одним из примеров применения специальных знаков является атрибут `Include` списков элементов. Например, в следующем списке элементов объявлено два элемента: `MyFile.cs` и `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Если требуется объявить элемент, содержащий точку с запятой в имени, следует использовать синтаксис %*xx*, чтобы экранировать точку с запятой и предотвратить объявление двух отдельных элементов в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Например, следующий элемент экранирует точку с запятой и объявляет один элемент с именем `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Использование специального знака MSBuild в качестве символа литерала  
  
-   Вместо специального знака используйте нотацию %*xx*, где *xx* представляет собой шестнадцатеричное значение символа ASCII. Например, чтобы использовать символ звездочки (*) как буквенный символ, используйте значение `%2A`.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)
 [Items](../msbuild/msbuild-items.md)
