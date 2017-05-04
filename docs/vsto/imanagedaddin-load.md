---
title: "IManagedAddin::Load | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin::Load"
  - "Load - метод"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  Вызывается при загрузке управляемой надстройки VSTO.  
  
## Синтаксис  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|*bstrManifestURL*|Полный путь манифеста для надстройки VSTO.|  
|*pdispApplication*|Указатель на IDispatch, представляющий ведущее приложение, загружающее надстройку VSTO.|  
  
## Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## Заметки  
 Манифест представляет собой файл \(как правило, XML\-файл\), предоставляющий сведения, используемые для загрузки надстройки VSTO. Например, манифест может указывать расположение сборки надстройки VSTO и класс точки входа для создания экземпляра при загрузке надстройки VSTO.  
  
 Параметр *bstrManifestURL* содержит значение записи `Manifest` в разделе реестра HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<имя приложения\>*\\Addins\\*\<ИД надстройки\>* для надстройки VSTO. Для получения дополнительной информации см. [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
 Реализуйте метод [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) для выполнения таких задач, как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.  
  
## См. также  
 [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  