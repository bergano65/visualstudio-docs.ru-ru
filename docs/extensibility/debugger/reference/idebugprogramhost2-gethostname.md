---
title: IDebugProgramHost2::GetHostName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45919c6c9fafceecca2cb53fa9c2c9f43b68e382
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870010"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Возвращает заголовок, понятное имя или имя файла, размещающего процесса данной программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

#### <a name="parameters"></a>Параметры
 `dwType`

 [in] Значение из [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) перечисления.

 `pbstrHostName`

 [out] Возвращает имя запрошенного размещающего процесса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В типичной реализации этого метода `dwType` параметр игнорируется, и возвращается понятное имя хост-компьютера. Другая возможная реализация является передача `dwType` параметр в вызов [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) метод для получения имени.

## <a name="see-also"></a>См. также
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)