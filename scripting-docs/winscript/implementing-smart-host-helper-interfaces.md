---
title: Реализация вспомогательных интерфейсов промежуточных узлов | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aff2d43d36fd543eea12d7fc60d3c56271af641
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088352"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Реализация вспомогательных интерфейсов промежуточных узлов
[Интерфейс IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) значительно упрощает задачу по созданию промежуточного узла для активной отладки, так как предоставляет реализации многих необходимых для этого интерфейсов.  
  
 Чтобы стать промежуточным узлом, используя `IDebugDocumentHelper`, ведущему приложению нужно выполнить три действия:  
  
1. Создать диспетчер отладки процессов с помощью `CoCreate` и использовать [интерфейс IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md), чтобы добавить приложение в список отлаживаемых.  
  
2. Создать вспомогательный объект документа отладки для каждого объекта скрипта с помощью метода [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md). Проверить, что документ, родительский документ, текст и блоки скриптов определены.  
  
3. Реализовать [интерфейс IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) для объекта, реализующего интерфейс [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) (это необходимо для активных скриптов). Единственный нетривиальный метод для интерфейса `IActiveScriptSiteDebug` просто делегирует вспомогательному объекту.  
  
   Кроме того, узел может реализовать [интерфейс IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md), если ему нужно дополнительно контролировать цвет синтаксиса, создание контекста документа и другие расширенные функции.  
  
   Основным ограничением вспомогательного объекта промежуточного узла является то, что он может обрабатывать только документы, содержимое которых изменилось или сжалось после их добавления (хотя документы могут и увеличиваться). Однако для многих промежуточных узлов предоставляемой функциональности совершенно достаточно.  
  
   В следующих разделах каждый из шагов описан более подробно.  
  
## <a name="create-an-application-object"></a>Создание объекта приложения  
 Прежде чем вспомогательный объект промежуточного узла можно будет использовать, нужно создать объект [интерфейса IDebugApplication](../winscript/reference/idebugapplication-interface.md), представляющий ваше приложение в отладчике.  
  
#### <a name="to-create-an-application-object"></a>Создание объекта приложения  
  
1.  Создайте экземпляр менеджера отладки процессов с помощью `CoCreateInstance`.  
  
2.  Вызовите [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Задайте имя для приложения с помощью [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Добавьте объект приложения в список отлаживаемых приложений с помощью [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Приведенный ниже код описывает этот процесс, однако в нем нет проверки ошибок или других методик робастного программирования.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Использование IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Использование вспомогательного объекта (минимальная последовательность шагов)  
  
1.  Для каждого документа узла создайте вспомогательный объект с помощью [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Вызовите [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) для вспомогательного узла, задав имя, атрибуты документа и т. д.  
  
3.  Вызовите [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) с родительским вспомогательным объектом для документа (или NULL, если документ является корневым), чтобы определить положение документа в дереве и сделать его видимым для отладчика.  
  
4.  Вызовите [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) или [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md), чтобы определить текст документа. (Их можно вызывать несколько раз, если документ загружается последовательно, как в случае с браузером.)  
  
5.  Вызовите [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md), чтобы определить диапазоны для каждого блока скрипта и связанных обработчиков скриптов.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Реализация IActiveScriptSiteDebug  
 Чтобы реализовать [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), получите вспомогательный объект, соответствующий заданному сайту, а затем начальное смещение документа для заданного контекста источника, как показано ниже:  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 После этого используйте вспомогательный объект, чтобы создать контекст документа для заданного смещения символов:  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Чтобы реализовать [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), просто вызовите `IDebugApplication::GetRootNode` (унаследован от [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Чтобы реализовать [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), просто возвратите изначально созданный `IDebugApplication`, используя диспетчер отладки процессов.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Необязательный интерфейс IDebugDocumentHost  
 Узел может предоставлять реализацию [интерфейса IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) с помощью [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md), чтобы расширить возможности управления вспомогательным объектом. Ниже перечислено несколько ключевых возможностей, предоставляемых интерфейсом узла:  
  
-   Добавление текста с помощью [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md), чтобы узлу не нужно было предоставлять фактические символы немедленно. Когда эти символы действительно необходимы, вспомогательный объект вызовет [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) на узле.  
  
-   Переопределение раскраски синтаксиса по умолчанию, предоставляемой вспомогательным объектом. Вспомогательный объект вызывает [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md), чтобы определить раскраску для диапазона символов, и возвращается к своей реализации по умолчанию, если узел возвращает `E_NOTIMPL`.  
  
-   Предоставьте управляющее unknown для контекстов документа, созданных вспомогательным объектом посредством реализации [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Это позволяет узлу переопределить функциональные возможности реализации контекста документа по умолчанию.  
  
-   Укажите путь в файловой системе для этого документа. Некоторые пользовательские интерфейсы отладки используют это, чтобы разрешить пользователям вносить и сохранять изменения в документе. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) вызывается, чтобы уведомить узел после сохранения документа.  
  
## <a name="see-also"></a>См. также раздел  
 [Обзор отладки активных скриптов](../winscript/active-script-debugging-overview.md)