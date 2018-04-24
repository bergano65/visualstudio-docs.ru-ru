---
title: Как обеспечить пропуск специальных знаков в MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e325ab2d5a5a54a9aaf8378753ccbe8f3a72a5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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
 [Элементы](../msbuild/msbuild-items.md) [MSBuild](../msbuild/msbuild.md)