---
title: "Справочник по неуправляемым интерфейсам API ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CleanOnlineAppCache [неуправляемое ClickOnce]"
  - "CleanOnlineAppCacheW - интерфейс [неуправляемое ClickOnce]"
  - "ClickOnce, неуправляемые API"
  - "GetDeploymentDataFromManifest [неуправляемое ClickOnce]"
  - "LaunchApplication [неуправляемое ClickOnce]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Справочник по неуправляемым интерфейсам API ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Неуправляемые открытые API [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] из библиотеки dfshim.dll.  
  
## CleanOnlineAppCache  
 Вызывает очистку или удаление всех подключенных приложений из кэша приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает значение типа HRESULT, представляющее тип сбоя.  При возникновении управляемого исключения возвращает значение 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
### Заметки  
 Вызов CleanOnlineAppCache приводит к запуску службы [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], если она еще не запущена.  
  
## GetDeploymentDataFromManifest  
 Возвращает информацию о развертывании из манифеста и URL\-адрес активации.  
  
### Параметры  
  
|Параметр|Описание|Тип|  
|--------------|--------------|---------|  
|`pcwzActivationUrl`|Указатель на объект `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Указатель на объект `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Указатель на буфер для приема строки с завершающим нулем, которая задает возвращаемую полную идентификацию приложения.|LPWSTR|  
|`pdwIdentityBufferLength`|Указатель на значение типа DWORD, представляющее длину буфера `pwzApplicationIdentity` в элементах WCHAR.  с учетом места для завершающего нуля.|LPDWORD|  
|`pwzProcessorArchitecture`|Указатель на буфер для приема строки с завершающим нулем, которая задает архитектуру процессора для развертывания приложения из манифеста.|LPWSTR|  
|`pdwArchitectureBufferLength`|Указатель на значение типа DWORD, представляющее длину буфера `pwzProcessorArchitecture` в элементах WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Указатель на буфер для приема строки с завершающим нулем, которая задает базу кода манифеста приложения из манифеста.|LPWSTR|  
|`pdwCodebaseBufferLength`|Указатель на значение типа DWORD, представляющее длину буфера `pwzApplicationManifestCodebase` в элементах WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Указатель на буфер для приема строки с завершающим нулем, которая задает поставщик развертывания из манифеста, если таковой имеется.  В противном случае возвращается пустая строка.|LPWSTR|  
|`pdwProviderBufferLength`|Указатель на значение типа DWORD, представляющее длину `pwzProviderBufferLength`.|LPDWORD|  
  
### Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает значение типа HRESULT, представляющее тип сбоя.  Возвращает HRESULTFROMWIN32 \(ERROR\_INSUFFICIENT\_BUFFER\), если буфер слишком мал.  
  
### Заметки  
 Указатели не должны принимать значение NULL.  `pcwzActivationUrl` и `pcwzPathToDeploymentManifest` не должны быть пустыми.  
  
 Очистка URL\-адреса активации должна производиться вызывающим кодом.  В частности, это касается добавления escape\-символов там, где они необходимы, или удаления строки запроса.  
  
 Проверка длины входных данных должна производиться вызывающим кодом.  Например, максимальная длина URL\-адреса составляет 2 КБ.  
  
## LaunchApplication  
 Вызывает запуск или установку приложения с использованием URL\-адреса развертывания.  
  
### Параметры  
  
|Параметр|Описание|Тип|  
|--------------|--------------|---------|  
|`deploymentUrl`|Указатель на строку с завершающим нулем, содержащую URL\-адрес манифеста развертывания.|LPCWSTR|  
|`data`|Зарезервировано для использования в будущем.  Должно иметь значение NULL.|LPVOID|  
|`flags`|Зарезервировано для использования в будущем.  Должно быть равно 0.|DWORD|  
  
### Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает значение типа HRESULT, представляющее тип сбоя.  При возникновении управляемого исключения возвращает значение 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
## См. также  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>