---
title: IDebugProcessSecurity::GetUserName | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94fcc74943deb33e7f98ba24e9d7389a9d5746fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Возвращает имя пользователя из поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrUserName`  
 [out] Строка, содержащая имя пользователя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод выполнен успешно, возвращается значение `S_OK`. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `GetUserName` Возвращает имя пользователя, который отображается в **имя пользователя** столбец **присоединиться к процессу** диалоговое окно. Чтобы просмотреть **присоединиться к процессу** диалоговое окно, нажмите кнопку **присоединиться к процессу** на **средства** меню в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE).  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)