---
title: '&lt;Элемент Schedules &gt; (начальный загрузчик) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85ffab2272a55bfe77c5f2a73c6e25967a203c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206095"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Элемент Schedules &gt; (начальный загрузчик)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Schedules`Элемент содержит `Schedule` элементы, которые определяют определенное время выполнения команд, определенных `Command` элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `Schedules`Элемент является дочерним по отношению к `Product` элементу. Каждый `Product` элемент может иметь не более одного `Schedules` элемента. У элемента `Schedules` нет атрибутов.  
  
## <a name="schedule"></a>Расписание  
 `Schedule`Элемент является дочерним по отношению к `Schedules` элементу. `Schedules`Элемент должен иметь по крайней мере один `Schedule` элемент.  
  
 `Schedule` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательный. Имя элемента расписания. Это соответствует `ScheduleName` свойству `Command` элемента. Когда объект `Command` ссылается на именованное расписание, он будет выполняться только в момент, указанный этим `Schedule` элементом. Расписания также могут быть связаны с `FailIf` элементами и `BypassIf` , которые ограничивают эти условные тесты для выполнения по указанному расписанию. Дополнительные сведения см. в разделе [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|  
  
 Данный `Schedule` элемент может иметь только один из следующих дочерних элементов.  
  
## <a name="buildlist"></a>буилдлист  
 `BuildList`Элемент указывает установщику выполнить команду сразу после запуска приложения начальной загрузки.  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`Элемент указывает установщику выполнить команду перед установкой указанного пакета.  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`Элемент указывает установщику выполнить команду после установки указанного пакета.  
  
## <a name="see-also"></a>См. также:  
 [\<Product> Дерев](../deployment/product-element-bootstrapper.md)   
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)
