---
title: 'AsyncTaskMethodBuilder внутренние элементы: структура | Документация Майкрософт'
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
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14b17ebde347d2558c8d18277d5c49d066243034
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572433"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Внутренние элементы: структура AsyncTaskMethodBuilder
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [AsyncTaskMethodBuilder внутренние элементы: структура](https://docs.microsoft.com/visualstudio/extensibility/debugger/asynctaskmethodbuilder-structure-internal-members).  
  
В этом разделе описывается внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> класс. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> справочника.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Внутренние элементы  
  
|name|Описание|  
|----------|-----------------|  
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя к отладчику.|  
|[поле m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Представляет обычный построитель объект, к которому делегирует этот экземпляр не являющегося универсальным.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

