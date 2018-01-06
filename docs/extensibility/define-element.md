---
title: "Определение элемента | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 35d33f0c440bce6d83c8a4712f0059d7f51a0ff0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="define-element"></a>Определение элемента
Определяет пару имя-значение символа. Этот символ может быть рассчитано условные атрибуты. Дополнительные сведения см. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md). См. также [символы элемент](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательно. Имя символа:<br /><br /> Имя = «Режим»|  
|value|Обязательно. Значение символа:<br /><br /> значение = «Standard»|  
|Условие|Необязательный. Дополнительные сведения см. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет интегрированную среду разработки (IDE). Например пункты меню, меню, панелей инструментов и поля со списком.|  
  
## <a name="example"></a>Пример  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)