---
title: Идебугженерикпарамфиелд | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95e1c4a7f4b6b8ba0b7f8ae70dbf04b29e83dc5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180673"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет параметр для универсального типа управляемого кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Используется для поддержки универсальных шаблонов.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам в интерфейсе [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Возвращает число ограничений, связанных с этим универсальным параметром.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Извлекает ограничения, связанные с этим универсальным параметром.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Получает флаги для этого универсального параметра.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Получает индекс этого универсального параметра.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Возвращает имя этого универсального параметра.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Возвращает владельца типа или метода этого универсального параметра.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
