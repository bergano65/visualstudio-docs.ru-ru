---
title: Интерфейс IDebugDocumentHost | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46684bf2264813a8daaa466b98119496ba85d4b9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346544"
---
# <a name="idebugdocumenthost-interface"></a>Интерфейс IDebugDocumentHost
Предоставляет функциональные возможности среды размещения, например раскраски синтаксиса, отладчику. `IDebugDocumentHelper::SetDebugDocumentHost` Метод принимает этот интерфейс в качестве аргумента.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentHost` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Возвращает диапазон символов, которые были добавлены с помощью `IDebugDocumentHelper::AddDeferredText`, в исходном документе узла.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Возвращает атрибуты текста для блока текста документа.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Уведомляет ведущее приложение, создается новый контекст документа и позволяет узлу, чтобы при необходимости вернуть объект, управляющий новый контекст.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Возвращает полный путь (включая имя файла) исходного файла документа.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Возвращает имя документа, без сведений о пути.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Уведомляет ведущее приложение, что был сохранен файл исходного документа, и что его содержимое должно обновляться.|