---
title: Элемент extern | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bac2f7e5611e8e87dd3ad6c268c0fd2ea6292c14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924195"
---
# <a name="extern-element"></a>Элемент extern
Элемент Extern ссылается на любой внешний заголовок (*.h*) файлов для слияния с *.vsct* файл во время компиляции. Файлы для объединения должны находиться в качестве пути включения для компилятора VSCT или с помощью [элемент Include](../extensibility/include-element.md). Файлы могут быть другие *.vsct* файлы или файлы заголовков C++.  
  
 Определения в файлах заголовков, должны быть в формате «#define [символ] [значение]» значение может быть другой символ, если оно определено ранее. Определения можно использовать в условных инструкциях, команда элементов. Любой символ, фактически не используется, будут отменены.  
  
 Элемент CommandTable  
Элемент Extern  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|href|Обязательный. Путь к файлу заголовка:<br /><br /> href="stdidcmd.h"|  
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|язык|Необязательный параметр. Язык по умолчанию для всех [ \<строки >](../extensibility/strings-element.md) элементы в таблице команд:<br /><br /> language="en-us"|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|Отсутствует.|Отсутствует.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды — то есть пунктов меню, меню, панелей инструментов и поля со списком, что VSPackage предоставляет интегрированную среду разработки.|  
  
## <a name="example"></a>Пример  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>См. также  
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)