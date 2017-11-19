---
title: "Включить элемент | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 818b56963c4733ef9bcf826b14df5a703c44e429
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="include-element"></a>Включить элемент
Элемент Include указывает файл, который можно найти на указанном экземпляре включать путь для вставки в текущий файл.  Все символы и типы, определенные станут частью скомпилированный результат.  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
<Include href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|href|Обязательный. Путь к файлу заголовка:<br /><br /> href="stdidcmd.h»|  
|Условие|Необязательно. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Отсутствует.|Отсутствует.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды — то есть элементы меню, меню, панели инструментов и поля со списком, который пакет VSPackage предоставляет интегрированную среду разработки.|  
  
## <a name="example"></a>Пример  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)