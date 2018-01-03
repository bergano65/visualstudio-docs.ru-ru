---
title: "Пошаговое руководство по Инструментам Visual Studio для Unity в Azure. Мобильный клиент | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 451b4f1f2580a55077bf3fc6a9ad3f16a2afaf0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Реализация Azure MobileServiceClient

Ключевое место в пакете SDK мобильного клиента Azure занимает <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a>, обеспечивающий доступ к серверной части мобильного приложения.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Поиск URL-адреса серверной части мобильного приложения

Конструктор `MobileServiceClient` принимает URL-адрес мобильного приложения в качестве параметра, поэтому сначала нужно найти этот URL-адрес.

1. На портале Azure нажмите кнопку **Службы приложений**.

    ![Щелкните "Службы приложений"](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Щелкните запись для своего мобильного приложения.

    ![Щелкните "Мобильное приложение"](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Скопируйте URL-адрес серверной части мобильного приложения.

    ![Скопируйте URL-адрес](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Создание одноэлементного MobileServiceClient

Должен присутствовать всего один экземпляр `MobileServiceClient`, поэтому в этом руководстве используется разновидность одноэлементного шаблона.

1. В каталоге **Assets/Scripts** своего проекта Unity создайте скрипта C# с именем **AzureMobileServiceClient**.

2. Откройте этот скрипт `AzureMobileServiceClient` и удалите весь имеющийся код шаблона, включая операторы using и объявление класса.

3. Добавьте следующий код:

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Если IntelliSense не распознает пространство имен Microsoft.WindowsAzure, убедитесь, что выполнены все шаги из раздела [Подготовка среды разработки]().

4. В приведенном выше коде замените `MOBILE_APP_URL` на URL-адрес серверной части мобильного приложения.

## <a name="next-step"></a>Дальнейшие действия

* [Обновление хранилища сертификатов безопасности Unity Mono](visual-studio-tools-for-unity-azure-security.md)
