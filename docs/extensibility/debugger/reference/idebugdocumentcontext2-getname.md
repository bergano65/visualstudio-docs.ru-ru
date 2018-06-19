---
title: IDebugDocumentContext2::GetName | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ded573db818b2343c13a8618f5b76323b8543a96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105753"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Возвращает отображаемое имя документа, который содержит контекст этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `gnType`  
 [in] Значение из [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) перечисления, указывающее тип возвращаемого имени.  
  
 `pbstrFileName`  
 [out] Возвращает имя файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обычно перенаправляет вызов [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) метод, если контекст документа не были записаны для хранения имя документа (как показано на примере).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CDebugContext` объекта, который предоставляет [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейса.  
  
```cpp  
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)    
{    
   HRESULT hr;    
  
   // Check for a valid file name argument.    
   if (pbstrFileName)    
   {    
      *pbstrFileName = NULL;    
  
      switch (gnType)    
      {    
         case GN_NAME:    
         case GN_FILENAME:    
         {    
            // Copy the member file name into the local file name.    
            *pbstrFileName = SysAllocString(m_sbstrFileName);    
            // Check for successful copy.    
            hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;    
            break;    
         }    
         default:    
         {    
            hr = E_FAIL;    
            break;    
         }    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)