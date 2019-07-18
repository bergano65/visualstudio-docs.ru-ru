---
title: IDebugProgramNode2::GetProgramName | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c46cb55140159bff12d297adbc5c0346ffe0409
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148551"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
```cpp#  
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
