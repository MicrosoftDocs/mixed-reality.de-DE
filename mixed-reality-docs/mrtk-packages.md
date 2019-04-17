---
title: MRTK Pakete
description: Dieser Artikel beschreibt die Pakete, die die Microsoft Mixed Reality Toollkit umfassen.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, Komponente, Paket
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604644"
---
# <a name="mrtk-packages"></a><span data-ttu-id="201f7-104">MRTK Pakete</span><span class="sxs-lookup"><span data-stu-id="201f7-104">MRTK packages</span></span>

<span data-ttu-id="201f7-105">Mixed Reality-Toolkit (MRTK) ist eine Auflistung von Paketen, die Entwicklung von plattformübergreifenden Mixed Reality-Anwendungen zu ermöglichen, durch die Unterstützung für Mixed Reality-Hardware und Plattformen Weise eine in Komponenten gegliederten.</span><span class="sxs-lookup"><span data-stu-id="201f7-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="201f7-106">Es gibt drei Kategorien von MRTK Pakete:</span><span class="sxs-lookup"><span data-stu-id="201f7-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="201f7-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="201f7-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="201f7-108">Erweiterung</span><span class="sxs-lookup"><span data-stu-id="201f7-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="201f7-109">Experimentelle</span><span class="sxs-lookup"><span data-stu-id="201f7-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="201f7-110">Foundation-Pakete</span><span class="sxs-lookup"><span data-stu-id="201f7-110">Foundation Packages</span></span>

<span data-ttu-id="201f7-111">Mixed Reality Toolkit Grundlage ist die Reihe von Paketen, mit die Ihre Anwendung für die allgemeine Funktionalität für Mixed Reality-Plattformen nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="201f7-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="201f7-112">Diese Pakete veröffentlicht werden, und aus dem Quellcode in von Microsoft unterstützt die [Mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) Branch auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="201f7-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK Foundation Pakete](images/mrtk-foundation.jpg)

<span data-ttu-id="201f7-114">*Mixed Reality-Toolkit-Foundation-Pakete*</span><span class="sxs-lookup"><span data-stu-id="201f7-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="201f7-115">Die Grundlage MRTK besteht aus:</span><span class="sxs-lookup"><span data-stu-id="201f7-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="201f7-116">Core-Paket</span><span class="sxs-lookup"><span data-stu-id="201f7-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="201f7-117">Plattformanbietern</span><span class="sxs-lookup"><span data-stu-id="201f7-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="201f7-118">Systemdienste</span><span class="sxs-lookup"><span data-stu-id="201f7-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="201f7-119">Feature-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="201f7-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="201f7-120">Die folgenden Abschnitte beschreiben die Typen von Paketen in jeder Kategorie.</span><span class="sxs-lookup"><span data-stu-id="201f7-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="201f7-121">Core-Paket</span><span class="sxs-lookup"><span data-stu-id="201f7-121">Core Package</span></span>

<span data-ttu-id="201f7-122">Das Core-Paket ist eine _erforderlichen_ Komponente und wird als eine Abhängigkeit von allen MRTK Foundation-Paketen.</span><span class="sxs-lookup"><span data-stu-id="201f7-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="201f7-123">Das Paket MRTK Core enthält:</span><span class="sxs-lookup"><span data-stu-id="201f7-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="201f7-124">Allgemeine Schnittstellen, Klassen und -Datentypen</span><span class="sxs-lookup"><span data-stu-id="201f7-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="201f7-125">MixedRealityToolkit Szene-Komponente</span><span class="sxs-lookup"><span data-stu-id="201f7-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="201f7-126">MRTK Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="201f7-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="201f7-127">Unity-Eingabeprovider</span><span class="sxs-lookup"><span data-stu-id="201f7-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="201f7-128">Paketverwaltung</span><span class="sxs-lookup"><span data-stu-id="201f7-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="201f7-129">Allgemeine Schnittstellen, Klassen und -Datentypen</span><span class="sxs-lookup"><span data-stu-id="201f7-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="201f7-130">Das Mixed Reality-Toolkit-Core-Paket enthält die Definitionen aller die gemeinsamen Schnittstellen, Klassen und Datentypen, die von allen anderen Komponenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="201f7-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="201f7-131">Es wird dringend empfohlen, dass Anwendungen MRTK Komponenten ausschließlich über die definierten Schnittstellen, damit die höchste Ebene der Kompatibilität auf Plattformen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="201f7-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="201f7-132">MixedRealityToolkit Szene-Komponente</span><span class="sxs-lookup"><span data-stu-id="201f7-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="201f7-133">Die MixedRealityToolkit-Szene-Komponente ist der einzelnen, zentralisierten Manager für das Mixed Reality-Toolkit.</span><span class="sxs-lookup"><span data-stu-id="201f7-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="201f7-134">Diese Komponente lädt und verwaltet die Lebensdauer der Plattform- und Module und bietet Ressourcen für die Systeme auf ihre Konfigurationseinstellungen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="201f7-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="201f7-135">MRTK Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="201f7-135">MRTK Standard Shader</span></span>

<span data-ttu-id="201f7-136">Der Standard-Shader von MRTK bildet die Grundlage für praktisch alle der Materialien, die von der MRTK bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="201f7-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="201f7-137">Dieser Shader ist äußerst flexibel und optimiert für die Vielzahl von Plattformen, die auf denen MRTK unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="201f7-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="201f7-138">Es ist _hoch_ empfohlen, dass es sich bei Ihrer Anwendung Materialien zu den standardmäßigen MRTK-Shader für eine optimale Leistung verwenden.</span><span class="sxs-lookup"><span data-stu-id="201f7-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="201f7-139">Unity-Eingabeprovider</span><span class="sxs-lookup"><span data-stu-id="201f7-139">Unity Input Provider</span></span>

<span data-ttu-id="201f7-140">Der Unity-Eingabe-Anbieter ermöglicht den Zugriff auf allgemeine Eingabegeräte wie z. B. Gamecontroller, Touchscreens und 3D räumliche Maus.</span><span class="sxs-lookup"><span data-stu-id="201f7-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="201f7-141">Paketverwaltung</span><span class="sxs-lookup"><span data-stu-id="201f7-141">Package Management</span></span>

<span data-ttu-id="201f7-142">_In Kürze verfügbar_</span><span class="sxs-lookup"><span data-stu-id="201f7-142">_Coming soon_</span></span>

<span data-ttu-id="201f7-143">Das Mixed Reality-Toolkit-Core-Paket bietet Unterstützung für das Erkennen und verwalten die optionale Foundation, Erweiterung und experimentelle MRTK Pakete.</span><span class="sxs-lookup"><span data-stu-id="201f7-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="201f7-144">Plattformanbietern</span><span class="sxs-lookup"><span data-stu-id="201f7-144">Platform Providers</span></span>

<span data-ttu-id="201f7-145">Der Anbieter MRTK-Pakete sind die Komponenten, mit denen die Mixed Reality-Toolkit für Ziel Mixed Reality-Hardware und Plattformfunktionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="201f7-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="201f7-146">Den unterstützten Plattformen gehören:</span><span class="sxs-lookup"><span data-stu-id="201f7-146">Supported platforms include:</span></span>

* [<span data-ttu-id="201f7-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="201f7-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="201f7-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="201f7-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="201f7-149">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="201f7-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="201f7-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="201f7-150">Windows Mixed Reality</span></span>

<span data-ttu-id="201f7-151">Das Paket Windows Mixed Reality bietet Unterstützung für Microsoft HoloLens und Windows Mixed Reality Immersive-Geräte.</span><span class="sxs-lookup"><span data-stu-id="201f7-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="201f7-152">Das Paket enthält die vollständige plattformunterstützung, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="201f7-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="201f7-153">Blicke für</span><span class="sxs-lookup"><span data-stu-id="201f7-153">Gaze targeting</span></span>
* <span data-ttu-id="201f7-154">Gesten</span><span class="sxs-lookup"><span data-stu-id="201f7-154">Gestures</span></span>
* <span data-ttu-id="201f7-155">Windows Mixed Reality-Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="201f7-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="201f7-156">Räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="201f7-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="201f7-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="201f7-157">OpenVR</span></span>

<span data-ttu-id="201f7-158">Das Paket OpenVR bietet Hardware- und Plattforminformationen für Geräte, die mithilfe der OpenVR-Plattform.</span><span class="sxs-lookup"><span data-stu-id="201f7-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="201f7-159">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="201f7-159">Windows Voice</span></span>

<span data-ttu-id="201f7-160">Das Windows-Voice-Paket bietet Unterstützung für Schlüsselwort Erkennung und Diktat-Funktionalität auf Microsoft Windows 10-Geräten.</span><span class="sxs-lookup"><span data-stu-id="201f7-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="201f7-161">Systemdienste</span><span class="sxs-lookup"><span data-stu-id="201f7-161">System Services</span></span>

<span data-ttu-id="201f7-162">Core Platform-Dienste werden in System Service-Paketen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="201f7-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="201f7-163">Diese Pakete enthalten das Mixed Reality-Toolkit-standardimplementierungen der System-Dienstschnittstellen, definiert der [Core](#core-package) Paket.</span><span class="sxs-lookup"><span data-stu-id="201f7-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="201f7-164">Die Grundlage MRTK umfasst die folgenden Dienste:</span><span class="sxs-lookup"><span data-stu-id="201f7-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="201f7-165">Grenze-System</span><span class="sxs-lookup"><span data-stu-id="201f7-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="201f7-166">Diagnosesystem</span><span class="sxs-lookup"><span data-stu-id="201f7-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="201f7-167">Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="201f7-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="201f7-168">Räumliche Awareness-System</span><span class="sxs-lookup"><span data-stu-id="201f7-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="201f7-169">Teleport System</span><span class="sxs-lookup"><span data-stu-id="201f7-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="201f7-170">Grenze-System</span><span class="sxs-lookup"><span data-stu-id="201f7-170">Boundary System</span></span>

<span data-ttu-id="201f7-171">Das MRTK Grenze System liefern Daten über die auf virtuelle Realität Playspace.</span><span class="sxs-lookup"><span data-stu-id="201f7-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="201f7-172">Auf Systemen, die für die der Benutzer die Grenze konfiguriert hat, kann das System eine Ebene Floor, rechteckigen Playspace, überwachte Bereich und mehr bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="201f7-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="201f7-173">Diagnosesystem</span><span class="sxs-lookup"><span data-stu-id="201f7-173">Diagnostic System</span></span>

<span data-ttu-id="201f7-174">Das Diagnosesystem MRTK bietet Echtzeit-Leistungsdaten in Ihrer anwendungsumgebung.</span><span class="sxs-lookup"><span data-stu-id="201f7-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="201f7-175">Auf einer Reihe werden Sie Framerate, Prozessorzeit und andere wichtige Leistungsmetriken anzeigen, wie Sie Ihre Anwendung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="201f7-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="201f7-176">Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="201f7-176">Input System</span></span>

<span data-ttu-id="201f7-177">MRTK Eingabesysteme ermöglicht die Eingabe in einer plattformübergreifenden Weise den Zugriff auf die durch Benutzeraktionen angeben, und weisen diese Aktionen zu den am besten geeigneten Schaltflächen und die Achsen für Ziel-Controller.</span><span class="sxs-lookup"><span data-stu-id="201f7-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="201f7-178">Räumliche Awareness-System</span><span class="sxs-lookup"><span data-stu-id="201f7-178">Spatial Awareness System</span></span>

<span data-ttu-id="201f7-179">Das räumliche MRTK-Awareness-System ermöglicht Zugriff auf realen Umgebungsdaten, von Geräten, z. B. die Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="201f7-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="201f7-180">Teleport System</span><span class="sxs-lookup"><span data-stu-id="201f7-180">Teleport System</span></span>

<span data-ttu-id="201f7-181">Das MRTK Teleport System unterstützt virtuelle Realität Locomotion.</span><span class="sxs-lookup"><span data-stu-id="201f7-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="201f7-182">Feature-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="201f7-182">Feature Assets</span></span>

<span data-ttu-id="201f7-183">Feature-Ressourcen handelt es sich um Sammlungen von verwandte Funktionen, die als Unity-Objekte und Skripts bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="201f7-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="201f7-184">Zu diesen Features zählen:</span><span class="sxs-lookup"><span data-stu-id="201f7-184">Some of these features include:</span></span>

* <span data-ttu-id="201f7-185">Steuerelemente der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="201f7-185">User Interface Controls</span></span>
* <span data-ttu-id="201f7-186">Standard-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="201f7-186">Standard Assets</span></span>
* <span data-ttu-id="201f7-187">more</span><span class="sxs-lookup"><span data-stu-id="201f7-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="201f7-188">Erweiterungspakete</span><span class="sxs-lookup"><span data-stu-id="201f7-188">Extension Packages</span></span>

<span data-ttu-id="201f7-189">Erweiterungspakete MRTK sind eine Auflistung von Paketen, die von Microsoft und der Community geschrieben, die erweitert und verbessert die Funktionalität des Mixed Reality-Toolkits.</span><span class="sxs-lookup"><span data-stu-id="201f7-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="201f7-190">Erweiterungsautoren Status alle erforderlichen Abhängigkeiten, markiert das Paket als kompatibel mit dem Mixed Reality-Toolkit und geben Sie die Lizenzierung und Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="201f7-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="201f7-191">Erweiterungspakete werden möglicherweise neue Features und neue plattformunterstützung bieten.</span><span class="sxs-lookup"><span data-stu-id="201f7-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="201f7-192">Im Laufe der Zeit können Extensions mit der Unterstützung und die Genehmigung der Autoren, in der Foundation MRTK migriert werden zu diesem, die Zeitpunkt sie freigegeben und von Microsoft unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="201f7-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![Erweiterungspaket MRTK](images/mrtk-extensions.jpg)

<span data-ttu-id="201f7-194">*Mixed Reality-Toolkit-Erweiterung Pakete*</span><span class="sxs-lookup"><span data-stu-id="201f7-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="201f7-195">Experimentelle Pakete</span><span class="sxs-lookup"><span data-stu-id="201f7-195">Experimental Packages</span></span>

<span data-ttu-id="201f7-196">Experimentelle Pakete bieten die Möglichkeit, Prototypfunktionen ein Flug, Vorabversionen und aufregende neue Ideen.</span><span class="sxs-lookup"><span data-stu-id="201f7-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="201f7-197">Das Ziel der meisten experimentelle Pakete ist etwas Neues aus, und Kunden zu messen.</span><span class="sxs-lookup"><span data-stu-id="201f7-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="201f7-198">Viele, aber nicht alle experimentellen werden Pakete neu veröffentlicht als Erweiterungen nach Abschluss der Erstellung von Prototypen und Testphase.</span><span class="sxs-lookup"><span data-stu-id="201f7-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![Experimentelle MRTK-Pakete](images/mrtk-experimental.jpg)

<span data-ttu-id="201f7-200">*Mixed Reality-Toolkit experimentelle Pakete*</span><span class="sxs-lookup"><span data-stu-id="201f7-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="201f7-201">Schlussbemerkung</span><span class="sxs-lookup"><span data-stu-id="201f7-201">Conclusion</span></span>

<span data-ttu-id="201f7-202">Die Mixed Reality-Toolkit-Paket und das paketverwaltungssystem dienen zum Aktivieren einer klaren und einfachen Methode für lichtdurchlässigen Funktionen in Ihre Lösungen zu erstellen, ohne dass nicht benötigte Komponenten, die in das Projekt eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="201f7-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="201f7-203">Im Laufe der Zeit wird Support für Paket hinzugefügt und im Mixed Reality-Toolkit erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="201f7-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="201f7-204">Wenn Sie Feedback oder beteiligten abrufen möchten, besuchen Sie bitte die [Mixed Reality-Toolkit-Project](https://github.com/Microsoft/MixedRealityToolkit-Unity) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="201f7-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="201f7-205">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="201f7-205">See also</span></span>

* [<span data-ttu-id="201f7-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="201f7-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

