---
title: 'IDebugObject2:: Исенкаутдатед | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa4acd0476a0df75644738840da562db97a34bf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842604"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод определяет, устарело ли состояние "изменить и продолжить" данного объекта или родительского контейнера. Пользовательский оценщик выражений не реализует этот метод и всегда возвращает `E_NOTIMPL` .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfEncOutdated`  
 заполняет Ненулевое значение ( `TRUE` ), если состояние "изменить и продолжить" устарело, ноль ( `FALSE` ), если нет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
> [!NOTE]
> Пользовательский оценщик выражений должен всегда возвращать значение `E_NOTIMPL` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
