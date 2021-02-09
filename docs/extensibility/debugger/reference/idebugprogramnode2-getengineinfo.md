---
title: 'IDebugProgramNode2:: Жетенгинеинфо | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b337d9c6742c1c3b0379a757761955151cc6dc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898647"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Возвращает имя и идентификатор модуля отладки (DE), выполняющего программу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Параметры
`pbstrEngine`\
заполняет Возвращает имя выключения программы (зависит от языка C++. это может быть пустой указатель, указывающий на то, что вызывающий объект не заинтересован в имени подсистемы).

`pguidEngine`\
заполняет Возвращает глобальный уникальный идентификатор для отключения программы (относящийся к C++: это может быть пустой указатель, указывающий, что вызывающий объект не заинтересован в идентификаторе GUID подсистемы).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
