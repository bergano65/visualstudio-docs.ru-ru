---
title: IDebugProcessSecurity::GetUserName | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe52eb2f90d6d957132d56313f1636d058e1bd0e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200659"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя пользователя от поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Если метод завершается успешно, возвращается `S_OK`. В противном случае он возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `GetUserName` Возвращает имя пользователя, который отображается в **имя пользователя** столбец **присоединение к процессу** диалоговое окно. Чтобы просмотреть **присоединение к процессу** диалоговом окне щелкните **присоединение к процессу** на **средства** меню в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] интегрированной среды разработки (IDE).  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

