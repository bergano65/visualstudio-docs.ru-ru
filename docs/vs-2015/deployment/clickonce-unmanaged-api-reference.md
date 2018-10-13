---
title: ClickOnce Справочник по неуправляемым API | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6175ae0b51e017d9f06c1e185ba1da7295d69657
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237560"
---
# <a name="clickonce-unmanaged-api-reference"></a>Справочник по неуправляемым интерфейсам API ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] неуправляемые открытый API из библиотеки dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Очищает или удаление всех подключенных приложений из [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] кэш приложения.  
  
### <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает значение HRESULT, представляющее тип сбоя. При возникновении управляемого исключения возвращается значение 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Примечания  
 Вызов CleanOnlineAppCache начнет [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] службы, если она еще не запущена.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Извлекает сведения о развертывании из манифеста и активации URL-адрес.  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|Тип|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Указатель на `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Указатель на `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Указатель на буфер для получения нулем строка, указывающая, возвращаются полную идентификацию приложения.|LPWSTR|  
|`pdwIdentityBufferLength`|Указатель на значение типа DWORD, который представляет собой длину `pwzApplicationIdentity` буфера в WCHARs. Сюда входит пространство для завершающего нуля.|LPDWORD|  
|`pwzProcessorArchitecture`|Указатель на буфер для получения ЗАКАНЧИВАЮЩУЮСЯ нулем строку, которая задает архитектуру процессора для развертывания приложения из манифеста.|LPWSTR|  
|`pdwArchitectureBufferLength`|Указатель на значение типа DWORD, который представляет собой длину `pwzProcessorArchitecture` буфера в WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Указатель на буфер для получения нулем строка, указывающая базу кода манифест приложения из манифеста.|LPWSTR|  
|`pdwCodebaseBufferLength`|Указатель на значение типа DWORD, который представляет собой длину `pwzApplicationManifestCodebase` буфера в WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Указатель на буфер для получения ЗАКАНЧИВАЮЩУЮСЯ нулем строку, которая указывает поставщик развертывания из манифеста, при его наличии. В противном случае возвращается пустая строка.|LPWSTR|  
|`pdwProviderBufferLength`|Указатель на значение типа DWORD, который представляет собой длину `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает значение HRESULT, представляющее тип сбоя. Возвращает HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER), если буфер слишком мал.  
  
### <a name="remarks"></a>Примечания  
 Указатели не должны иметь значение null. `pcwzActivationUrl` и `pcwzPathToDeploymentManifest` не должно быть пустым.  
  
 Это обязанность вызывающего для очистки, URL-адрес активации. Например это касается добавления escape-символов где они необходимы, или удаления строки запроса.  
  
 Это обязанность вызывающего для ограничения длины входных данных. Например Максимальная длина URL-адреса составляет 2 КБ.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Запускает или установку приложения с помощью URL-адрес развертывания.  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|Тип|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Указатель на ЗАКАНЧИВАЮЩУЮСЯ нулем строку, которая содержит URL-адрес манифеста развертывания.|LPCWSTR|  
|`data`|Зарезервировано для будущего использования. Должен иметь значение NULL.|LPVOID|  
|`flags`|Зарезервировано для будущего использования. Должно быть 0.|DWORD|  
  
### <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает значение HRESULT, представляющее тип сбоя. При возникновении управляемого исключения возвращается значение 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>



