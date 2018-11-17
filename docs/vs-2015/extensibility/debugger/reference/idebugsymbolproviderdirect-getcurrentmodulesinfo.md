---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Документация Майкрософт
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
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bca8c1ee258c14f3114a9a62e791a7d6a3bade68
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767891"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает сведения о модулях в группе символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```csharp  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCount`  
 [in] Число модулей в `ppGuids` массива.  
  
 `ppGuids`  
 [in] Массив, содержащий уникальные идентификаторы для модулей.  
  
 `pADIds`  
 [in] Идентификаторы доменов приложений.  
  
 `pCurrentState`  
 [in] Текущее состояние группы символов.  
  
 `ppCDModItfs`  
 [out] Возвращает объект, содержащий модули в группе символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

