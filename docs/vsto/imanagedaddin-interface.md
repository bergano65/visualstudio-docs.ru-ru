---
title: IManagedAddin - интерфейс
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f29356a3e11634d742d6f6022c35cf8f10871eec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddin-interface"></a>IManagedAddin - интерфейс
  Реализуйте интерфейс IManagedAddin для создания компонента, который загружает управляемые надстройки VSTO. Этот интерфейс был добавлен в выпуске 2007 системы Microsoft Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```c++
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
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы, которые определены в интерфейс IManagedAddin.  
  
|name|Описание|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Вызывается, когда приложение Microsoft Office загружает управляемую надстройку VSTO.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Вызывается непосредственно перед тем, как приложение Microsoft Office выгружает управляемую надстройку VSTO.|  
  
## <a name="remarks"></a>Примечания  
 Приложения Microsoft Office, начиная с выпуска 2007 системы Microsoft Office, использовать интерфейс IManagedAddin, помогая загружать надстройки Office VSTO. Можно реализовать интерфейс IManagedAddin для создания собственного загрузчика надстройки VSTO и среды выполнения для управляемых надстроек VSTO, вместо использования загрузчика надстройки VSTO (*VSTOLoader.dll*) и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Для получения дополнительной информации см. [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Способ загрузки управляемых надстроек  
 При запуске приложения происходит следующее.  
  
1.  Приложение обнаруживает надстройки VSTO путем поиска записей в следующем разделе реестра:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<имя приложения >_ \Addins\**  
  
     Каждая запись в этом разделе реестра представляет собой уникальный идентификатор надстройки VSTO. Как правило, это имя сборки надстройки VSTO.  
  
2.  Приложение ищет запись `Manifest` под записью для каждой надстройки VSTO.  
  
     Управляемые надстройки VSTO могут хранить полный путь манифеста в `Manifest` запись в **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<имя приложения >_ \Addins\\  _\<ИД надстройки >_**. Манифест представляет собой файл (как правило, XML-файл), предоставляющий сведения, используемые для загрузки надстройки VSTO.  
  
3.  Если приложение находит запись `Manifest` , приложение пытается загрузить компонент загрузчика управляемой надстройки VSTO. Приложение делает это, пытаясь создать COM-объект, реализующий интерфейс IManagedAddin.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Включает компонент загрузчика надстройки VSTO (*VSTOLoader.dll*), или можно создать свой собственный интерфейс IManagedAddin реализации.  
  
4.  Приложение вызывает метод [IManagedAddin::Load](../vsto/imanagedaddin-load.md) и передает в него значение записи `Manifest` .  
  
5.  Метод [IManagedAddin::Load](../vsto/imanagedaddin-load.md) выполняет задачи, необходимые для загрузки надстройки VSTO, такие как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.  
  
 Дополнительные сведения о реестре ключи, которые используются приложениями Microsoft Office для обнаружения и загрузки управляемых надстроек VSTO см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-to-implement-imanagedaddin"></a>Руководство по реализации IManagedAddin  
 При реализации IManagedAddin необходимо зарегистрировать библиотеку DLL, содержащую реализацию с помощью следующего идентификатора CLSID:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Этот идентификатор CLSID используется приложениями Microsoft Office для создания COM-объекта, который реализует IManagedAddin.  
  
> [!CAUTION]  
>  Этот идентификатор CLSID также используется *VSTOLoader.dll* в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Таким образом, при использовании IManagedAddin для создания собственного загрузчика надстроек VSTO и компонент среды выполнения не может развертывать этот компонент на компьютерах под управлением надстроек VSTO, которые зависят от [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-Интерфейс неуправляемого &#40;разработка решений Office в Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  