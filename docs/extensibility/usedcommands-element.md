---
title: "Элемент Используемыхкоманд | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a51359a840812bc20714df91a3357801366f3616
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="usedcommands-element"></a>Элемент Используемыхкоманд
Элемент Используемыхкоманд группирует элементы Используемойкоманды и других Используемыхкоманд группирований.  
  
 Элемент Используемыхкоманд является необязательным. Если не нужно вызывать команды, определенные вне пакета, у вас для включения в vsct-файл в этом разделе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Условие|Необязательно. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент UsedCommand](../extensibility/usedcommand-element.md)|Команда, которая реализуется другим кодом.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды (например, пункты меню, меню, панелей инструментов и поля со списком), которые VSPackage предоставляет интегрированную среду разработки (IDE).|  
  
## <a name="example"></a>Пример  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент Используемойкоманды](../extensibility/usedcommand-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)