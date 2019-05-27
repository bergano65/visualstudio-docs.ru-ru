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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 65bc4e95fbf73517e4f247a60404eff9e6747ef7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206953"
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

## <a name="parameters"></a>Параметры
`pAddress`\
[in] Отладка адрес, представленный [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

`pGuid`\
[out] Уникальный идентификатор модуля.

`pAppID`\
[out] Идентификатор домена приложения.

`pTokenClass`\
[out] Токен, представляющий содержащего класса.

`pTokenMethod`\
[out] Токен, представляющий модуль.

`pdwOffset`\
[out] Смещение в байтах от начала `pAddress` параметра.

`pdwVersion`\
[out] Номер версии метода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)