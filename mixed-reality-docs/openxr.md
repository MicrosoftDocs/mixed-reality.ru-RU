---
title: опенкср
description: Создайте подсистему с помощью переносимого стандарта API Опенкср и разверните его на гарнитурах Windows Mixed Reality и HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя
ms.openlocfilehash: 8a3cfef506f47a7cc49bff2851b9fc14c8a830b4
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160010"
---
# <a name="openxr"></a>опенкср

Опенкср — это открытый стандарт API из <a href="https://www.khronos.org/" target="_blank">кхронос</a> , который предоставляет механизмам собственный доступ к широкому спектру устройств от многих поставщиков, охватывающих спектр различных [типов](mixed-reality.md).

Вы можете разрабатывать приложения с помощью Опенкср на виртуальной головной гарнитуре HoloLens 2 или Windows Mixed Reality на рабочем столе.  Если у вас нет доступа к гарнитуре, можно использовать эмулятор HoloLens 2 или симулятор Windows Mixed Reality.

## <a name="why-openxr"></a>Зачем Опенкср?

С помощью Опенкср вы можете создавать обработчики, предназначенные как для holographic устройств (например, HoloLens 2), которые размещают цифровое содержимое в реальном мире, как если бы оно было на самом деле, а также как впечатляющие устройства (например, гарнитуры Windows Mixed Reality для настольных ПК), которые скрывают физические мир и замените его цифровой опытом.  Опенкср позволяет написать код, который затем будет переносимым на широком диапазоне аппаратных платформ.

API Опенкср использует загрузчик, который подключает ваше приложение непосредственно к поддержке собственной платформы вашей гарнитуры.  Это обеспечивает максимальную производительность и минимальную задержку конечных пользователей независимо от того, используете ли они гарнитуру Windows Mixed Reality или любую другую гарнитуру.

## <a name="what-is-openxr"></a>Что такое Опенкср?

API Опенкср предоставляет основные функции прогнозирования, работы с рамками и использования пространственных входных данных. вам потребуется создать подсистему, предназначенную для таких устройств, как HoloLens 2 и иммерсивное устройство, например гарнитуры Windows Mixed Reality.

Чтобы узнать об API Опенкср, ознакомьтесь со <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификацией</a>опенкср 1,0, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">справочником по API</a> и <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">кратким справочником</a>.  Дополнительные сведения см. на <a href="https://www.khronos.org/openxr/" target="_blank">странице Кхронос опенкср</a>.

Чтобы ориентироваться на полный набор функций HoloLens 2, вы также будете использовать расширения Опенкср, относящиеся к поставщику и поставщику, которые предоставляют дополнительные функции за пределами ядра Опенкср 1,0, такие как отслеживание, отслеживание глаз, пространственное сопоставление и пространственные привязки.  Дополнительные сведения о расширениях, которые появятся позже в этом году, см. в [разделе о планах](#roadmap) .

Обратите внимание, что Опенкср не является механизмом смешанной реальности.  Вместо этого Опенкср позволяет использовать такие модули, как Unity и Нереал, для написания переносимого кода, который затем может получить доступ к функциям собственной платформы в holographic или иммерсивное устройство пользователя независимо от того, какой поставщик создал эту платформу.

## <a name="roadmap"></a>Путеводитель

Спецификация Опенкср определяет механизм расширения, позволяющий разработчикам среды выполнения предоставлять дополнительные функциональные возможности за пределами [основных функций](#what-is-openxr) , определенных в <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">базовой спецификации опенкср 1,0</a>.

Существует три вида расширений Опенкср:
* **Расширения поставщика (например, `MSFT`):** Включает инновации каждого поставщика в функции оборудования или программного обеспечения.  Любой поставщик среды выполнения может в любое время внедрить и поставлять расширение поставщика.
  * **Экспериментальные расширения поставщиков (например, `MSFT_preview`):** Экспериментальные расширения поставщиков, которые можно просмотреть для сбора отзывов.  расширения `MSFT_preview` предназначены только для устройств разработчика и будут удалены при поставке настоящего расширения.  Чтобы поэкспериментировать с ними, можно [включить расширения предварительного просмотра на устройстве разработчика](openxr-getting-started.md#using-preview-extensions).
* **Расширения `EXT` для разных поставщиков:** Расширения кросс-поставщика, которые определяются и реализуются несколькими компаниями.  Группы заинтересованных компаний могут в любое время внедрять расширения EXT.
* **Официальные расширения `KHR`:** Официальные расширения Кхронос ратифицирован в рамках основной версии спецификации.  Расширения КХР охватываются той же лицензией, что и Основная спецификация.

По состоянию на июль 2020 среда выполнения Windows Mixed Reality будет поддерживать набор `MSFT` и `EXT` расширений, которые предоставляют полный набор функций HoloLens 2 для Опенкср приложений:

| Область применения компонента | Доступность расширения |
|--------------|------------------------|
| Системы + сеансы | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code> <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Справочные пространства (Просмотр, локальный, этап)](coordinate-systems.md) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Просмотр конфигураций (моно, стерео) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Время кадров](understanding-performance-for-mixed-reality.md) + [цепочек переключений](rendering.md) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Слои композиции<br />(проекция, четыре) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Входные и хаптикс](interaction-fundamentals.md) | **Базовая спецификация Опенкср 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Интеграция Direct3D 11 | **Выпущено официальное расширение `KHR`:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code><br /> |
| Интеграция Direct3D 12 | **Определено официальное расширение `KHR`:** *(пока не поддерживается)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**Поддержка предварительной версии**: Апрель 2020 *(запланированная)*</p><p>**Полная поддержка**: Май 2020 *(запланированная)*</p> |
| [Несвязанное пространство ссылок<br />(возможности мирового масштаба)](coordinate-systems.md#building-a-world-scale-experience) | **выпущенное расширение `MSFT`:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Пространственные привязки](spatial-anchors.md) | **выпущенное расширение `MSFT`:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [<br />взаимодействие вручную (захват/AIM, воздушный, с проводами)](hands-and-tools.md) | **доступно расширение `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_interaction_preview">XR_MSFT_hand_interaction_preview</a></code><p>**выпуск`MSFT`** : Апрель 2020 *(запланированная)*</p> |
| [Сетка руки артикулатион +](hands-and-tools.md) | **доступно расширение `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>**выпуск`MSFT`** : Май 2020 *(запланированная)*</p> |
| Взаимодействие с другими пакетами SDK для HoloLens (например, [QR](qr-code-tracking.md)) | **доступно расширение `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>**выпуск`MSFT`** : Май 2020 *(запланированная)*</p> |
| [Отслеживание глаз](eye-tracking.md) | <p>**`MSFT_preview`** : Апрель 2020 *(запланированный)*</p><p>**выпуск`MSFT` или `EXT`** : Май 2020 *(запланированная)*</p> |
| [<br />записи смешанной реальности (третья Визуализация с камеры PV)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) | **доступно расширение `MSFT_preview`:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><br /><p>**выпуск`MSFT`** : Июнь 2020 *(запланированный)*</p> |
| [Модели отрисовки контроллера движения](motion-controllers.md#rendering-the-motion-controller-model) | <p>**`MSFT_preview`** : Апрель 2020 *(запланированный)*</p><p>**выпуск`MSFT`** : Июль 2020 *(запланированный)*</p> |
| [Основные сведения о сцене (плоскости, сетки)](scene-understanding.md) | <p>**`MSFT_preview`** : Май 2020 *(запланированная)*</p><p>**выпуск`MSFT`** : Июль 2020 *(запланированный)*</p> |

Хотя некоторые из этих расширений могут запускаться как зависящие от поставщика `MSFT`ные расширения, корпорация Майкрософт и другие поставщики среды выполнения Опенкср работают вместе для проектирования расширений `EXT` или `KHR` для многих из этих функциональных областей.  Это обеспечит переносимость кода, который вы пишете для этих функций, между поставщиками среды выполнения, как и в случае с основной спецификацией.

## <a name="get-started-with-openxr"></a>Начало работы с Опенкср

Вы можете разрабатывать приложения с помощью Опенкср на виртуальной головной гарнитуре HoloLens 2 или Windows Mixed Reality на рабочем столе.  Если у вас нет доступа к гарнитуре, можно использовать эмулятор HoloLens 2 или симулятор Windows Mixed Reality.

Чтобы приступить к разработке приложений Опенкср для HoloLens 2 или впечатляющих головных телефонов Windows Mixed Reality, см. статью как приступить к разработке [опенкср](openxr-getting-started.md).

## <a name="see-also"></a>См. также:

* <a href="https://www.khronos.org/openxr/" target="_blank">Дополнительные сведения о Опенкср</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Спецификация Опенкср 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Справочник по API Опенкср 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Краткое справочное руководство по Опенкср 1,0</a>
