---
title: Элемент extern | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dce51835164424272874b42b6073131607c7272
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573519"
---
# <a name="extern-element"></a>Элемент Extern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент Extern](https://docs.microsoft.com/visualstudio/extensibility/extern-element).  
  
Элемент Extern ссылается на файлы внешних заголовков (h) можно объединить с vsct-файл во время компиляции. Файлы для объединения должны находиться в качестве пути включения для компилятора VSCT или с помощью [включают элемент](../extensibility/include-element.md). Файлы могут быть другие vsct-файлы или файлы заголовков C++.  
  
 Определения в файлах заголовков, должны быть в формате «#define [символ] [значение]» значение может быть другой символ, если оно определено ранее. Определения можно использовать в условных инструкциях, команда элементов. Любой символ, фактически не используется, будут отменены.  
  
 Элемент CommandTable  
Элемент Extern  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|href|Обязательно. Путь к файлу заголовка:<br /><br /> href="stdidcmd.h»|  
|Условие|Необязательный. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|язык|Необязательный. Язык по умолчанию для всех [ \<строки >](../extensibility/strings-element.md) элементы в таблице команд:<br /><br /> Language = "en-us»|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Отсутствует.|Отсутствует.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды — то есть пунктов меню, меню, панелей инструментов и поля со списком, что VSPackage предоставляет интегрированную среду разработки.|  
  
## <a name="example"></a>Пример  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Command Table (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)

