---
title: "Элемент Используемойкоманды | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b3974c9103a385badc56fda759ee95ef3a40a93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="usedcommand-element"></a>Элемент Используемойкоманды
Позволяет VSPackage для доступа к команде, которая определена в другой файл vsct. Например, если пакет VSPackage использует стандарт **копирования** команду, которая определяется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочки, можно добавить команды меню или панель инструментов без повторной реализации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID пары идентификатор GUID, который определяет команду.|  
|id|Обязательный. Идентификатор пары идентификатор GUID, который определяет команду.|  
|Условие|Необязательно. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Группирует элементы Используемойкоманды и других Используемыхкоманд группирований.|  
  
## <a name="remarks"></a>Примечания  
 Добавив команду, чтобы `<UsedCommands>` уведомляет VSPackage элемент, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среде, что VSPackage требуется команда. Следует добавить `<UsedCommand>` элемент для любой команды, пакет необходимо, могут не включаться во всех версиях и конфигурации Visual Studio. Например, если пакет вызывает команду, которая относится к Visual C++, команда будет недоступен для пользователей Visual Web Developer, если не включить `<UsedCommand>` элемент для команды.  
  
## <a name="example"></a>Пример  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент Используемыхкоманд](../extensibility/usedcommands-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)