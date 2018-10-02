---
title: 'AsyncTaskMethodBuilder&lt;TResult&gt; внутренние элементы: структура | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 644d4907fc32e823fff0a7e5ea0dd29d34973b8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572944"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; внутренние элементы: структура
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [AsyncTaskMethodBuilder&lt;TResult&gt; внутренние элементы: структура](https://docs.microsoft.com/visualstudio/extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members).  
  
В этом разделе описывается внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> класс. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> справочника.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Внутренние элементы  
  
|name|Описание|  
|----------|-----------------|  
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя к отладчику.|  
|[поле m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Представляет отложенной инициализацией встроенных задач.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

