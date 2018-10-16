---
title: Как обеспечить пропуск специальных знаков в MSBuild | Документы Майкрософт
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
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8346d44b16e9ada275541a23c4bf080ef1f0f54a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230179"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Как обеспечить пропуск специальных знаков в MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Некоторые символы имеют особое значение в файлах проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. К ним относятся точка с запятой (;) и звездочка (*). Полный список таких специальных знаков см. в разделе [Специальные символы в MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Чтобы использовать эти специальные знаки в качестве литералов в файле проекта, их необходимо задать с помощью синтаксиса %*xx*, где *xx* представляет шестнадцатеричное значение ASCII знака.  
  
## <a name="msbuild-special-characters"></a>Специальные символы в MSBuild  
 Одним из примеров применения специальных знаков является атрибут `Include` списков элементов. Например, в следующем списке элементов объявлено два элемента: `MyFile.cs` и `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Если требуется объявить элемент, содержащий точку с запятой в имени, следует использовать синтаксис %*xx*, чтобы экранировать точку с запятой и предотвратить объявление двух отдельных элементов в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Например, следующий элемент экранирует точку с запятой и объявляет один элемент с именем `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Использование специального знака MSBuild в качестве символа литерала  
  
-   Вместо специального знака используйте нотацию %*xx*, где *xx* представляет собой шестнадцатеричное значение символа ASCII. Например, чтобы использовать символ звездочки (*) как буквенный символ, используйте значение `%2A`.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Элементы](../msbuild/msbuild-items.md) [MSBuild](msbuild.md)


