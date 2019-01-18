---
title: Установка Visual Studio 2017 для Mac
description: Инструкции по установке Visual Studio для Mac и дополнительных компонентов, которые требуются для кроссплатформенной разработки.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: ca24c09a0eedc9aee10a4fad8ceb126a2d72462a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315812"
---
# <a name="install-visual-studio-2017-for-mac"></a>Установка Visual Studio 2017 для Mac

## <a name="requirements"></a>Требования

Чтобы приступить к разработке собственных кроссплатформенных приложений, нужно установить и настроить несколько компонентов при скачивании Visual Studio для Mac.

Для работы с iOS в Visual Studio необходимы следующие компоненты:

- Компьютер Mac с macOS Sierra 10.12 или более поздней версии
- Xcode 8.3 или более поздней версии. Обычно рекомендуется использовать последнюю стабильную версию.
- Идентификатор Apple ID. Если у вас нет идентификатора Apple ID, его можно создать на сайте https://appleid.apple.com. Он необходим для установки приложения Xcode и входа в него.

> [!NOTE]
> Visual Studio 2019 для Mac (предварительная версия) [теперь доступна](installation.md?view=vsmac-2019) для установки тестирования.

## <a name="install"></a>Установка

1. Скачайте Visual Studio для Mac на сайте [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/).

2. После скачивания пакета установщика щелкните файл **VisualStudioForMacInstaller.dmg**, чтобы подключить установщик, а затем запустите его, дважды щелкнув логотип, как показано на следующем рисунке:

   ![Диалоговое окно установщика](media/installer-image1.png)

3. Может отобразиться диалоговое окно оповещения, как на следующем рисунке. В этом случае нажмите кнопку **Открыть**:

   ![диалоговое окно оповещения](media/installer-image2.png)

4. Установщик проверяет вашу систему, чтобы определить, какие компоненты требуется установить или обновить:

   ![Оценка системы](media/installer-image3.png)

5. После этого отображается диалоговое окно оповещения, предлагающее принять условия соглашения о конфиденциальности и лицензионного соглашения. Нажмите кнопку **Продолжить**, чтобы подтвердить условия:

   ![Диалоговое окно лицензии](media/installer-image4.png)

6. Установщик выводит список отсутствующих необходимых компонентов, которые нужно скачать и установить. Выберите продукты, которые хотите скачать:

   ![Выбор элементов](media/installer-image5.png)

   Если вы не хотите устанавливать все платформы, выберите нужные с помощью приведенных ниже рекомендаций.

   * **Приложения, использующие Xamarin**:
      - Xamarin.Forms — выберите платформы **Android** и **iOS**.
      - Только iOS — выберите платформу **iOS** (вам нужно также установить [**Xcode**](https://developer.apple.com/xcode/)).
      - Только Android — выберите платформу **Android** (вам нужно также выбрать соответствующие зависимости).
      - Только Mac— выберите платформу **macOS** (вам нужно также установить [**Xcode**](https://developer.apple.com/xcode/)).
      - Полностью кроссплатформенные приложения Xamarin — выберите платформы **Android**, **iOS** и **macOS**.
   * **Приложения .NET Core** — выберите платформу **.NET Core**.
   * **Веб-приложения ASP.NET Core** — выберите платформу **.NET Core**.
   * **Разработка кроссплатформенных игр Unity** — не нужно устанавливать дополнительные платформы, кроме Visual Studio для Mac. Дополнительные сведения об установке расширения Unity вы найдете в [руководстве по установке Unity](/visualstudio/macm/setup-vsmac-tools-unity).

   На этом экране установки отображается версия и размер каждого компонента. Вы можете щелкнуть каждый из компонентов, чтобы отобразить список его зависимостей (для Android), просмотреть скачиваемые им дополнительные пакеты (для .NET Core) или просмотреть обязательные дополнительные приложения (для iOS и macOS):

   ![Дополнительные зависимости для Android](media/installer-image6.png)

7. Выбрав требуемые параметры, нажмите кнопку **Установить и обновить** для запуска процесса установки.

8. Установщик начинает скачивать и устанавливать выбранные элементы:

   ![Запуск установки](media/installer-image7.png)

   ![Скачивание Xamarin.Mac](media/installer-image8.png)

   ![Завершение установки](media/installer-image9.png)

9. Вам может потребоваться повысить уровень разрешений для отдельных компонентов, которые необходимы для завершения установки. Чтобы продолжить процесс установки, введите учетные данные администратора:

   ![Предоставление разрешений для продолжения установки](media/installer-image10.png)

10. После успешной установки можно запустить приложения разработки в Visual Studio, нажав кнопку **Запустить**:

    ![Открытие Visual Studio](media/installer-image11.png)

> [!NOTE]
> Если вы решили не устанавливать платформу или инструмент в рамках исходной установки (отменив выбор этого элемента на шаге 6), позже для установки этих компонентов потребуется снова запустить [установщик](https://visualstudio.microsoft.com/vs/).

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Установка Visual Studio для Mac в среде, защищенной брандмауэром или прокси-сервером

Для установки Visual Studio для Mac в среде, защищенной брандмауэром, необходимо сделать доступными ряд конечных точек, чтобы разрешить скачивание необходимых средств и обновлений ПО.

Настройте сеть, разрешив доступ к следующим расположениям:

- [Конечные точки Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Следующие шаги

Установка Visual Studio для Mac позволяет перейти к написанию кода для приложений. Следующие руководства помогут вам в создании и развертывании проектов.

### <a name="ios"></a>iOS

1. [Привет, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Подготовка устройства](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (для запуска приложения на устройстве).

### <a name="android"></a>Android

1. [Использование диспетчера пакетов SDK Android для Xamarin](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Эмулятор SDK для Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Настройка устройства для разработки](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Приложения .NET Core, веб-приложения ASP.NET Core, разработка игр Unity

Другие рабочие нагрузки описаны [на этой странице](/visualstudio/mac/workloads).

## <a name="see-also"></a>См. также

- [Установка Visual Studio 2017 (в Windows)](/visualstudio/install/install-visual-studio)
