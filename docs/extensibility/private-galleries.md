---
title: Частные галереи Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: afd1d79d7f1846e60386d2a9478466bf7eae72e4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444652"
---
# <a name="private-galleries"></a>Частные галереи
Вы можете поделиться элементами управления, шаблонами и инструментами, которые вы разрабатываете, разместив их в *частной галерее* в интрасети для вашей организации, следующим образом:

- Создайте канал Atom (RSS) для подходяще настроенного центрального местоположения (репозитория) в интрасети. Для получения дополнительной информации [см. Как: Создать атомный канал для частной галереи](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Распространяйте файл *.pkgdef,* описывающий частную галерею. Мы рекомендуем эту конфигурацию для администраторов, которые хотят подключить частную галерею к многим компьютерам одновременно.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Добавьте частную галерею к расширениям и обновлениям в Visual Studio
 Когда доступна частная галерея, вы можете добавить ее в **расширения и обновления** в Visual Studio.

 ![Диалоговое окно "Добавить" диспетчера расширений](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Добавление частной галереи в расширения и обновления

1. В строке меню выберите **Сервис** > **Параметры**.

2. В узло **окружающей среды** выберите **расширения и обновления.**

3. и нажмите кнопку **Добавить**.

4. В поле **«Имя»** введите название для `My Gallery`частной галереи, например, .

5. В поле **URL** введите URL-адрес канала Atom или сайта SharePoint, на размещении которого находится частная галерея.

    1. Если хост является атомом, который подключается к частной `http://www.mywebsite/mygallery/atom.xml`галерее, URL будет напоминать этот: .  Этот URL-адрес может относиться к файлу или сетевому пути.

    2. Если хост является сайтом SharePoint, URL `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`будет напоминать этот: .

### <a name="manage-private-galleries"></a>Управление частными галереями
 Администратор может сделать частную галерею доступной для нескольких компьютеров одновременно, изменив системный реестр на каждом компьютере. Для достижения этой цели создайте файл *.pkgdef,* описывающий новые ключи реестра и их значения.  Формат этого файла заключается в следующем.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Для получения дополнительной [информации см. Как: Управление частной галереей с помощью настроек реестра](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Установка расширений из частной галереи
 Вы можете искать и устанавливать расширения Visual Studio из частной галереи в **расширениях и обновлениях.** Следующие шаги используют частную галерею под названием `My Gallery`.

 ![Диспетчер расширений устанавливает закрытую галерею](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Поиск и установка расширений из частной галереи

1. В меню-баре выберите **«Инструменты** > **расширения и обновления».**

2. В левой панели выберите **расширения в Интернете,** а затем выберите **My Gallery.**

3. В правильном стеку выберите расширение, а затем выберите кнопку **Загрузка.**

## <a name="update-extensions-from-a-private-gallery"></a>Расширение обновления из частной галереи
 Поскольку новые версии расширений Visual Studio размещаются в частной галерее, вы можете обновить установленные расширения. Следующие шаги используют частную галерею под названием `My Repository`.

 ![Обновление закрытой галереи диспетчера расширений](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Обновление установленного расширения из частной галереи

1. В меню-баре выберите **«Инструменты** > **расширения и обновления».**

2. В левом стеле выберите **обновления,** а затем выберите **Мой репозиторий.**

3. В правом стеле выберите расширение, а затем выберите кнопку **обновления.**

## <a name="see-also"></a>См. также
- [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Расширение визуальной студии ship](../extensibility/shipping-visual-studio-extensions.md)
