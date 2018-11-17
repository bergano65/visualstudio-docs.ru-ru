---
title: IDebugGenericParamField | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e433d3cde52d51460a9387164239186e47c1b60b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722802"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет параметр универсального типа управляемого кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Используется для поддержки универсальных типов.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Возвращает количество ограничений, связанных с этим универсальным параметром.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Получает ограничения, связанные с этим универсальным параметром.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Извлекает флаги для данного универсального параметра.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Извлекает индекс этого универсального параметра.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Получает имя этого универсального параметра.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Возвращает имя типа или метода владельца этого универсального параметра.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

