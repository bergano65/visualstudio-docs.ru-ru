---
title: Элемент Уседкомманд | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186364"
---
# <a name="usedcommand-element"></a>Элемент UsedCommand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Включает пакет VSPackage для доступа к команде, определенной в другом vsct-файле. Например, если пакет VSPackage использует стандартную команду **Copy** , определяемую [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] оболочкой, можно добавить команду в меню или на панель инструментов без повторной реализации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID пары ИДЕНТИФИКАТОРов GUID, определяющей команду.|  
|идентификатор|Обязательный. Идентификатор пары ИДЕНТИФИКАТОРов GUID, определяющей команду.|  
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Группирует элементы Уседкомманд и другие группирования Уседкоммандс.|  
  
## <a name="remarks"></a>Remarks  
 Добавив команду в `<UsedCommands>` элемент, VSPackage информирует [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] среду о том, что пакету VSPackage требуется команда. Необходимо добавить `<UsedCommand>` элемент для любой команды, которая требуется для пакета, которая может не включаться во все версии и конфигурации Visual Studio. Например, если пакет вызывает команду, относящуюся к Visual C++, команда будет недоступна пользователям Visual Web Developer, если не включить `<UsedCommand>` элемент для команды.  
  
## <a name="example"></a>Пример  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>См. также:  
 [Уседкоммандс, элемент](../extensibility/usedcommands-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
