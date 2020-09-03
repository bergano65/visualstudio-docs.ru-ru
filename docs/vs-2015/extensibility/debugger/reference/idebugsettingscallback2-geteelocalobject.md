---
title: 'IDebugSettingsCallback2:: Жетилокалобжект | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e6bf186d8b4bf660cc4a22e962754e859378674
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202483"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает локальный объект средства оценки выражений по заданному имени метрики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetEELocalObject(  
   REFGUID     guidLang,  
   REFGUID     guidVendor,  
   LPCWSTR     pszMetric,  
   IUnknown ** ppUnk  
);  
```  
  
```csharp  
private int GetEELocalObject(  
   ref Guid          guidLang,  
   ref Guid          guidVendor,  
   string            pszMetric,  
   out System.Object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidLang`  
 окне Уникальный идентификатор языка программирования.  
  
 `guidVendor`  
 окне Уникальный идентификатор поставщика.  
  
 `pszMetric`  
 окне Имя метрики.  
  
 `ppUnk`  
 заполняет Возвращает локальный объект средства оценки выражений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
