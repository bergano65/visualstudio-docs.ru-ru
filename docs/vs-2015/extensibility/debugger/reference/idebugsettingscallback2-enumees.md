---
title: 'IDebugSettingsCallback2:: Енумис | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cca998c4cdae8cc5e543a24a5cdfe18369e51b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155214"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Перечисляет доступные средства оценки выражений по идентификаторам языка и поставщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```csharp  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celtBuffer`  
 окне Число элементов в `pceltEEs` буфере.  
  
 `rgguidLang`  
 [вход, выход] Уникальный идентификатор языка программирования.  
  
 `rgguidVendor`  
 [вход, выход] Уникальный идентификатор поставщика.  
  
 `pceltEEs`  
 [вход, выход] Массив средств оценки выражений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
