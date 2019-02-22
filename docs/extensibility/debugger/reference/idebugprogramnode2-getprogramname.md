---
title: IDebugProgramNode2::GetProgramName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6f678adc135e85f8808cef36d819733033447e4
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450377"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Возвращает имя программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

#### <a name="parameters"></a>Параметры
`pbstrProgramName`  
[out] Возвращает имя программы.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Имя программы не то же самое, что путь к программе, несмотря на то, что имя программы может быть частью такой путь.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CProgram` объект, реализующий [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс. `MakeBstr` Функция выделяет копию указанной строки как BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>См. также
[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
