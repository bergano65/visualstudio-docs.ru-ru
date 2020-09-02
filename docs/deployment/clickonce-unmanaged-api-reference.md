---
title: Справочник по неуправляемым API для ClickOnce | Документация Майкрософт
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900283"
---
# <a name="clickonce-unmanaged-api-reference"></a>Справочник по неуправляемым интерфейсам API ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] неуправляемые открытые API из dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Очищает или удаляет все интерактивные приложения из [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] кэша приложений.

### <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает значение HRESULT, представляющее сбой. При возникновении управляемого исключения возвращает 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Remarks
 Вызов Клеанонлинеаппкаче приведет к запуску [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] службы, если она еще не запущена.

## <a name="getdeploymentdatafrommanifest"></a>жетдеплойментдатафромманифест
 Извлекает сведения о развертывании из манифеста и URL-адреса активации.

### <a name="parameters"></a>Параметры

|Параметр|Описание|Тип|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Указатель на объект `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Указатель на объект `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Указатель на буфер, получающий строку, завершающуюся НУЛЕМ, которая указывает возвращаемое полное удостоверение приложения.|LPWSTR|
|`pdwIdentityBufferLength`|Указатель на DWORD, который представляет собой длину `pwzApplicationIdentity` буфера в вчарс. Сюда входит пробел для завершающего символа NULL.|лпдворд|
|`pwzProcessorArchitecture`|Указатель на буфер для получения строки с завершающим НУЛЕМ, которая указывает архитектуру процессора для развертывания приложения, из манифеста.|LPWSTR|
|`pdwArchitectureBufferLength`|Указатель на DWORD, который представляет собой длину `pwzProcessorArchitecture` буфера в вчарс.|лпдворд|
|`pwzApplicationManifestCodebase`|Указатель на буфер для получения строки с завершающим НУЛЕМ, которая указывает базу кода манифеста приложения из манифеста.|LPWSTR|
|`pdwCodebaseBufferLength`|Указатель на DWORD, который представляет собой длину `pwzApplicationManifestCodebase` буфера в вчарс.|лпдворд|
|`pwzDeploymentProvider`|Указатель на буфер для получения строки, завершающейся НУЛЕМ, которая указывает поставщика развертывания из манифеста, если он есть. В противном случае возвращается пустая строка.|LPWSTR|
|`pdwProviderBufferLength`|Указатель на DWORD, который является длиной `pwzProviderBufferLength` .|лпдворд|

### <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает значение HRESULT, представляющее сбой. Возвращает HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER), если буфер слишком мал.

### <a name="remarks"></a>Remarks
 Указатели не должны иметь значение null. `pcwzActivationUrl` и `pcwzPathToDeploymentManifest` не должен быть пустым.

 Он отвечает за очистку URL-адреса активации. Например, добавьте escape-символы, где они требуются, или удалите строку запроса.

 Это обязанность вызывающего объекта ограничивать длину входных данных. Например, максимальная длина URL-адреса — 2 КБ.

## <a name="launchapplication"></a>лаунчаппликатион
 Запускает или устанавливает приложение с помощью URL-адреса развертывания.

### <a name="parameters"></a>Параметры

|Параметр|Описание|Тип|
|---------------|-----------------|----------|
|`deploymentUrl`|Указатель на строку, завершающуюся нулем, которая содержит URL-адрес манифеста развертывания.|LPCWSTR|
|`data`|Зарезервировано для будущего использования. Должен иметь значение NULL.|лпвоид|
|`flags`|Зарезервировано для будущего использования. Должно быть равно 0.|DWORD|

### <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает значение HRESULT, представляющее сбой. При возникновении управляемого исключения возвращает 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>См. также раздел
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>