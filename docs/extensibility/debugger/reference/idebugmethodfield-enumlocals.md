---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "Метод IDebugMethodField::EnumLocals"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает перечислитель для выбранных локальных переменных метода.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Параметры  
 `pAddress`  
 \[in\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект, представляющий адрес отладки, который выбирает контекст или область, из которого следует получать локальные переменные.  
  
 `ppLocals`  
 \[out\] возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список локальных; в противном случае возвращает значение NULL, если локальные переменные.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK и возвращает значение S\_FALSE, если локальные переменные.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Только перечисляются переменные, определенные внутри блока, содержащий отладочные заданным адресом.  Если все локальные включая любые локальные значения, создаваемые компилятором требуются, вызовите [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) метод.  
  
 Метод может содержать несколько блоков контекстов или области.  Например, следующий ухитренный метод содержит саму 3 области, 2 внутренних и тело блока метода.  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) представляет объект  `func` сам метод.  Вызов `EnumLocals` метод с  [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) значение  `Inner Scope 1` адрес возвращает содержать перечисления  `temp1` переменная, например.  
  
## См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)