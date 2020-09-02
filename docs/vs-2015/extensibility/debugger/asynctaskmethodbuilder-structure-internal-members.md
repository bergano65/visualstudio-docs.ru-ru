---
title: Структура AsyncTaskMethodBuilder — внутренние элементы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bfe640654c9de7daac9096aa4d75f5492a8a278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555916"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Внутренние элементы: структура AsyncTaskMethodBuilder
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В этом разделе описываются внутренние члены <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> класса. Общие сведения об этом классе см <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . в разделе справки.  
  
 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как вы не можете получить доступ к этим внутренним членам из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Внутренние элементы  
  
|Имя|Описание|  
|----------|-----------------|  
|[ObjectIdForDebugger, свойство](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя в отладчике.|  
|[m_builder поле](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Представляет объект универсального конструктора, для которого этот неуниверсальный экземпляр не является делегатом.|  
  
## <a name="see-also"></a>См. также:  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
