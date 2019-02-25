---
title: IDebugEngine2::SetRegistryRoot | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761a8509958c60746f7e5312fa5f5e13631acc7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698811"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Задает корневой элемент реестра для обработчика отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

#### <a name="parameters"></a>Параметры
 `pszRegistryRoot`

 [in] Корень реестра для использования.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод позволяет [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] для указания альтернативного корневая папка реестра, DE следует использовать для получения параметров реестра; например, «HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp».

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)