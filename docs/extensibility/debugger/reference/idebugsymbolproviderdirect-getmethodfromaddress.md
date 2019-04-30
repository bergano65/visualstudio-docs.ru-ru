---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0eecc7331bc510366cd012e30cc1088ef6c60da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868461"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Извлекает сведения о методе по адресу указанного отладки.

## <a name="syntax"></a>Синтаксис

```cpp
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

 [in] Отладка адрес, представленный [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

 `pGuid`

 [out] Уникальный идентификатор модуля.

 `pAppID`

 [out] Идентификатор домена приложения.

 `pTokenClass`

 [out] Токен, представляющий содержащего класса.

 `pTokenMethod`

 [out] Токен, представляющий модуль.

 `pdwOffset`

 [out] Смещение в байтах от начала `pAddress` параметра.

 `pdwVersion`

 [out] Номер версии метода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)