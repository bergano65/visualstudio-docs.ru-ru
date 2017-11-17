---
title: "Справочник по API неуправляемым ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 11e10800ff51abd6f95447d85204a44f8367f551
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>Справочник по неуправляемым интерфейсам API ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]неуправляемых открытых API из библиотеки dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Очищает или удаление всех подключенных приложений из [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] кэш приложения.  
  
### <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает значение HRESULT, представляющее тип сбоя. При возникновении управляемого исключения, возвращает значение 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Примечания  
 Вызов CleanOnlineAppCache начнет [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] службы, если он еще не запущен.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Извлекает сведения о развертывании из манифеста и активации URL-адрес.  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|Тип|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Указатель на `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Указатель на `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Указатель на буфер для получения нулем строка, указывающая, возвращаемую полную идентификацию приложения.|LPWSTR|  
|`pdwIdentityBufferLength`|Указатель на значение DWORD, длина `pwzApplicationIdentity` буфера в WCHARs. Это включает место для завершающего нуля.|LPDWORD|  
|`pwzProcessorArchitecture`|Указатель на буфер для приема нулем строки, которая задает архитектуру процессора для развертывания приложения из манифеста.|LPWSTR|  
|`pdwArchitectureBufferLength`|Указатель на значение DWORD, длина `pwzProcessorArchitecture` буфера в WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Указатель на буфер для получения нулем строка, указывающая codebase манифест приложения из манифеста.|LPWSTR|  
|`pdwCodebaseBufferLength`|Указатель на значение DWORD, длина `pwzApplicationManifestCodebase` буфера в WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Указатель на буфер для приема строки с завершающим нулем, которая указывает поставщик развертывания из манифеста, при его наличии. В противном случае возвращается пустая строка.|LPWSTR|  
|`pdwProviderBufferLength`|Указатель на значение DWORD, длина `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает значение HRESULT, представляющее тип сбоя. Возвращает HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER), если буфер слишком мал.  
  
### <a name="remarks"></a>Примечания  
 Указатели не должны иметь значение null. `pcwzActivationUrl`и `pcwzPathToDeploymentManifest` не может быть пустым.  
  
 Это вызывающим Очистка URL-адрес активации. Например это касается добавления escape-символов где они нужны или удаления строки запроса.  
  
 Вызывающий объект несет длины входных данных. Например Максимальная длина URL-адреса составляет 2 КБ.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Запуск или установка приложения с помощью URL-адрес развертывания.  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|Тип|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Указатель NULL нулевым байтом строка, содержащая URL-адрес манифеста развертывания.|LPCWSTR|  
|`data`|Зарезервировано для будущего использования. Должен иметь значение NULL.|LPVOID|  
|`flags`|Зарезервировано для будущего использования. Должно быть 0.|DWORD|  
  
### <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает значение HRESULT, представляющее тип сбоя. При возникновении управляемого исключения, возвращает значение 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>