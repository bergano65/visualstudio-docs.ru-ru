---
title: IActiveScriptStringCompare::StrComp | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStringCompare.StrComp
apilocation:
- scrobj.dll
helpviewer_keywords:
- StrComp method, IActiveScriptStringCompare interface
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b2fea6ae4d5819680f38d19f2cd6ea1cf9bf9b5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090107"
---
# <a name="iactivescriptstringcomparestrcomp"></a>IActiveScriptStringCompare::StrComp
Определяет метод сравнения строк для обработчика скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bszStr1`  
 Первая строка.  
  
 `bszStr2`  
 Вторая строка.  
  
 `iRet`  
 Результат сравнения. 0, если `bszStr1` и `bszStr2`идентичны; -1, если `bszStr1`  <  `bszStr2`; 1, если `bszStr1`  >  `bszStr2`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент является недопустимым.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается каждый раз, выполняемого сравнения строк.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как попытка перегрузки функции сравнения строк. При использовании перегрузки допускается [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) присвоить SCRIPTPROP_STRINGCOMPAREINSTANCE.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)