---
title: 'Идебугсимболпровидердирект:: Жетмесодфромаддресс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 16ba628887f1910738df825a0965959715c5d250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155115"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает сведения о методе по указанному адресу отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 окне Адрес отладки, представленный интерфейсом [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pGuid`  
 заполняет Уникальный идентификатор модуля.  
  
 `pAppID`  
 заполняет Идентификатор домена приложения.  
  
 `pTokenClass`  
 заполняет Токен, представляющий содержащий класс.  
  
 `pTokenMethod`  
 заполняет Токен, представляющий модуль.  
  
 `pdwOffset`  
 заполняет Смещение в байтах от начала `pAddress` параметра.  
  
 `pdwVersion`  
 заполняет Номер версии метода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
