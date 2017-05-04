---
title: "Интерфейс IManagedAddin | Microsoft Docs"
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
  - "IManagedAddin - интерфейс"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Интерфейс IManagedAddin
  Реализуйте интерфейс IManagedAddin для создания компонента, который загружает управляемые надстройки VSTO. Этот интерфейс был добавлен в выпуске 2007 системы Microsoft Office.  
  
## Синтаксис  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## Методы  
 В следующей таблице перечислены методы, которые задаются интерфейсом IManagedAddin.  
  
|Имя|Описание|  
|---------|--------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Вызывается, когда приложение Microsoft Office загружает управляемую надстройку VSTO.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Вызывается непосредственно перед тем, как приложение Microsoft Office выгружает управляемую надстройку VSTO.|  
  
## Заметки  
 Приложения Microsoft Office, начиная с выпуска 2007 системы Microsoft Office, используют интерфейс IManagedAddin для помощи в загрузке надстройки VSTO Office. Вы можете реализовать интерфейс IManagedAddin для создания собственного загрузчика надстроек VSTO и среды выполнения для управляемых надстроек VSTO вместо использования загрузчика надстроек VSTO \(VSTOLoader.dll\) и среды выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Для получения дополнительной информации см. [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
## Порядок загрузки управляемых надстроек  
 При запуске приложения происходит следующее.  
  
1.  Приложение обнаруживает надстройки VSTO путем поиска записей в следующем разделе реестра:  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<имя приложения\>*\\Addins\\  
  
     Каждая запись в этом разделе реестра представляет собой уникальный идентификатор надстройки VSTO. Как правило, это имя сборки надстройки VSTO.  
  
2.  Приложение ищет запись `Manifest` под записью для каждой надстройки VSTO.  
  
     Управляемые надстройки VSTO могут хранить полный путь манифеста в записи `Manifest` в разделе HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<имя приложения\>*\\Addins\\*\<ИД надстройки\>*. Манифест представляет собой файл \(как правило, XML\-файл\), предоставляющий сведения, используемые для загрузки надстройки VSTO.  
  
3.  Если приложение находит запись `Manifest`, приложение пытается загрузить компонент загрузчика управляемой надстройки VSTO. Приложение делает это, пытаясь создать COM\-объект, реализующий интерфейс IManagedAddin.  
  
     Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] включает компонент загрузчика надстройки VSTO \(VSTOLoader.dll\), или вы можете создать свой собственный загрузчик путем реализации интерфейса IManagedAddin.  
  
4.  Приложение вызывает метод [IManagedAddin::Load](../vsto/imanagedaddin-load.md) и передает в него значение записи `Manifest`.  
  
5.  Метод [IManagedAddin::Load](../vsto/imanagedaddin-load.md) выполняет задачи, необходимые для загрузки надстройки VSTO, такие как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.  
  
 Дополнительные сведения о разделах реестра, которые используются приложениями Microsoft Office для обнаружения и загрузки управляемых надстроек VSTO, см. в разделе [Записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Рекомендации по реализации IManagedAddin  
 При реализации IManagedAddin вы должны зарегистрировать библиотеку DLL, содержащую эту реализацию, с помощью следующего идентификатора CLSID:  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Этот идентификатор CLSID используется приложениями Microsoft Office для создания COM\-объекта, реализующего IManagedAddin.  
  
> [!CAUTION]  
>  Этот идентификатор CLSID также используется библиотекой VSTOLoader.dll в среде выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Таким образом, при использовании IManagedAddin для создания собственного компонента загрузчика и среды выполнения для надстройки VSTO вы не можете развертывать этот компонент на компьютерах, на которых работают надстройки VSTO на основе среды выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## См. также  
 [Справочные материалы по неуправляемым API &#40;разработка решений Office в Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  