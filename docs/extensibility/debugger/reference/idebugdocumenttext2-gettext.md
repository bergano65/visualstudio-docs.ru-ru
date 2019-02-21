---
title: IDebugDocumentText2::GetText | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 729b56b4161d6cfd38db91334427840d0c7339d8
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449663"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
Получение текста из указанной позиции в документе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetText(
    TEXT_POSITION pos,
    ULONG         cMaxChars,
    WCHAR*        pText,
    ULONG*        pcNumChars
);
```

```csharp
int GetText(
    eumn_TEXT_POSITION pos,
    uint               cMaxChars,
    IntPtr             pText,
    out uint           pcNumChars
);
```

#### <a name="parameters"></a>Параметры
`pos`  
[in] Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуру, которая указывает расположение текста, который требуется получить.

`cMaxChars`  
[in] Максимальное количество символов текста, который требуется получить.

`pText`  
[in, out] Указатель на буфер, который должен быть заполнен с помощью требуемый текст. Этот буфер должен иметь возможность содержать по крайней мере `cMaxChars` число расширенных символов.

`pcNumChars`  
[out] Возвращает число фактически полученных символов.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В этом примере показано, как этот метод может вызываться с помощью C#.

```csharp
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Debugger.Interop;

namespace Mynamespace
{
    class MyClass
    {
        string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)
        {
            string documentText = string.Empty;
            if (pText != null)
            {
                uint numLines = 0;
                uint numChars = 0;
                int hr;
                hr = pText.GetSize(ref numLines, ref numChars);
                if (ErrorHandler.Succeeded(hr))
                {
                    IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));
                    uint actualChars = 0;
                    hr = pText.GetText(pos, numChars, buffer, out actualChars);
                    if (ErrorHandler.Succeeded(hr))
                    {
                        documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);
                    }
                    Marshal.FreeCoTaskMem(buffer);
                }
            }
            return documentText;
        }
    }
}
```

## <a name="see-also"></a>См. также
[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)  
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
