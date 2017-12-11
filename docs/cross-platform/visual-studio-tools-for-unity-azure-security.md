---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по безопасности в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: d036d180fddcce443debe3d7917415380187994c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Обновление хранилища сертификатов безопасности Unity Mono

Unity Mono поставляется с пустым хранилищем сертификатов, поэтому все сайты являются ненадежными. Дополнительные сведения об этом см. на странице [вопросов и ответов о безопасности Mono](http://www.mono-project.com/docs/faq/security/).

Чтобы подключиться к Azure, не игнорируя TLS/SSL, необходимо обновить хранилище сертификатов Unity Mono.

## <a name="using-mozroots-to-install-certificates"></a>Установка сертификатов с помощью mozroots

В состав Mono входит средство mozroots. Оно скачивает и устанавливает список корневых сертификатов Mozilla.

1. Откройте терминал командной строки.

2. В терминале перейдите к каталогу **C:\Program Files\Unity\Editor\Data\MonoBleedingEdge\bin>**. Это расположение может быть другим в зависимости от места установки Unity на компьютере.

3. Введите следующую команду и нажмите клавишу **ВВОД**, чтобы выполнить ее:

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Должны быть получены следующие выходные данные (хотя число добавленных сертификатов может быть другим):

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. Теперь пример проекта должен выполняться без ошибок, связанных с TLS.

## <a name="next-step"></a>Дальнейшие действия

* [Тестирование клиентских подключений](visual-studio-tools-for-unity-azure-connection.md)
