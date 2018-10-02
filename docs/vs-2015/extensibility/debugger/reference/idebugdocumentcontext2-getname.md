---
title: IDebugDocumentContext2::GetName | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e3dc6b87227757aae4b9814b99aa93ec4c0d394
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564242"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugDocumentContext2::GetName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-getname).  
  
Возвращает отображаемое имя документа, который содержит контекст этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Значение из [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) перечисление, указывающее тип имени для возврата.  
  
 `pbstrFileName`  
 [out] Возвращает имя файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обычно перенаправляет вызов [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) метод, если контекст документа записывается для хранения имя документа (как в примере показано).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CDebugContext` объекта, который предоставляет [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс.  
  
```cpp#  
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

