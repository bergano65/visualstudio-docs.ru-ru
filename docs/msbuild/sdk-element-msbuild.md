---
title: Элемент SDK (MSBuild) | Документация Майкрософт
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d674e7613898816f905e0d0a11bdc2484cf4f25
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325327"
---
# <a name="sdk-element-msbuild"></a>Элемент SDK (MSBuild)
Ссылка на пакет SDK для проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<SDK>  


## <a name="syntax"></a>Синтаксис  

```xml  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание:|  
|---------------|-----------------|  
|`Name`|Обязательный атрибут.<br /><br /> Имя пакета SDK для проекта.|  
|`Version`|Необязательный атрибут.<br /><br /> Версия пакета SDK для проекта.|  

### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы  
 |Элемент|Описание:|  
|-------------|-----------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="see-also"></a>См. также  
 [How to: Use MSBuild Project SDKs](../msbuild/how-to-use-project-sdk.md)  (Практическое руководство. Использование пакета SDK проекта MSBuild)  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
