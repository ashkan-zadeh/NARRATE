# NARRATE

**N**aturalistic **A**ction **R**easoning and **R**eal-World **A**wareness **T**hrough **E**xplanations

**Paper title:** NARRATE: A Multimodal Real-World Australian Driving Dataset for Human-Centred Explanations in Automated Driving

**Ashkan Yousefi Zadeh**<sup>1,2</sup>, Zishuo Zhu<sup>1,2</sup>, Xiaomeng Li<sup>1,2</sup>, Andry Rakotonirainy<sup>1,2</sup>, Sebastien Glaser<sup>1,2</sup>, Ronald Schroeter<sup>1,2</sup>, Patricia Delhomme<sup>3</sup>, and Zahra Mehraban<sup>1,2</sup>

<sup>1</sup> Queensland University of Technology (QUT), Faculty of Health, School of Psychology and Counselling, Australia  
<sup>2</sup> ARC Training Centre for Automated Vehicles in Rural and Remote Regions (AVR3), Australia  
<sup>3</sup> Université Gustave Eiffel, Laboratory of Applied Psychology and Ergonomics, France

*European Conference on Computer Vision (ECCV) 2026 — DriveX: 6th Workshop on Foundation Models for Autonomous Driving (Archival Track)*

<p align="center">
  <a href="https://eccv.ecva.net"><img src="https://img.shields.io/badge/ECCV_2026-DriveX_Workshop-7B1FA2?style=flat"></a>
  <a href="https://arxiv.org/abs/2608.14767"><img src="https://img.shields.io/badge/arXiv-2608.14767-B31B1B?style=flat"></a>
  <a href="https://doi.org/10.25912/RDF_1786669427992"><img src="https://img.shields.io/badge/Dataset-QUT_Research_Data_Finder-2E7D32?style=flat"></a>
  <a href="https://doi.org/10.25912/RDF_1786669427992"><img src="https://img.shields.io/badge/DOI-10.25912%2FRDF__1786669427992-1565C0?style=flat"></a>
  <a href="https://ashk4n.me/projects/narrate/"><img src="https://img.shields.io/badge/Project_Page-ashk4n.me-E65100?style=flat"></a>
  <a href="https://creativecommons.org/licenses/by/4.0/"><img src="https://img.shields.io/badge/License-CC_BY_4.0-C62828?style=flat"></a>
</p>

<p align="center">
  <a href="https://github.com/ashkan-zadeh/NARRATE/blob/main/assets/NARRATE.mp4">
    <img src="assets/NARRATE_preview.gif" width="100%" alt="NARRATE dataset showcase — click to watch full video">
  </a>
</p>

![NARRATE dataset sample](assets/narrate_sample.png)

![NARRATE data collection setup](assets/data_collection.png)

NARRATE is a multimodal real-world driving dataset collected in Brisbane CBD, Queensland, Australia by Queensland University of Technology. The dataset was developed through the ARC Training Centre for Automated Vehicles in Rural and Remote Regions (AVR3).

NARRATE is designed to support research on human-centred explanations for automated driving. It captures driving events from experienced drivers and driving instructors on public roads, pairing synchronised vehicle sensor data with driver-produced explanations collected during the drive and/or during a post-drive video-cued interview.

The dataset contains 2,050 annotated driving events from 35 experienced drivers and driving instructors. Each event is grounded in multimodal sensor streams and includes annotations for driver action, driving scenario context, and Situational Awareness (SA).

## Access

The dataset files are not hosted in this GitHub repository.

Access to the NARRATE dataset is provided through mediated access via QUT Research Data Finder:

**[https://doi.org/10.25912/RDF_1786669427992](https://doi.org/10.25912/RDF_1786669427992)**

This repository provides dataset documentation, structure information, and usage notes for researchers who request access through the official data access pathway.

## Dataset Contents

The mediated-access release is organised as an anonymised publication package:

```text
front_camera/
front_left_camera/
front_right_camera/
rear_camera/
metadata_json/
sensor_bags/
```

All released event files use non-identifying anonymised event identifiers. Participant IDs, raw event IDs, local machine paths, and server paths are not included in the public file names.

## Camera Videos

The video folders contain event-level camera clips from the instrumented vehicle:

- `front_camera/`: forward-facing centre camera clips
- `front_left_camera/`: forward-left camera clips
- `front_right_camera/`: forward-right camera clips
- `rear_camera/`: rear-facing camera clips

Camera files are named using the anonymised event identifier and the camera view:

```text
abcd-0001_front_camera.mp4
abcd-0001_front_left_camera.mp4
abcd-0001_front_right_camera.mp4
abcd-0001_rear_camera.mp4
```

The camera clips are anonymised before release. Faces and licence plates are processed with automated video privacy blurring. Researchers should treat the release as a privacy-processed dataset and follow the access conditions provided through QUT Research Data Finder.

## Metadata

The `metadata_json/` folder contains event-level JSON metadata files. Each JSON file uses the anonymised event identifier:

```text
abcd-0001.json
```

The metadata connects an event to its available video and sensor assets and stores the event annotations, explanation text, timing information, kinematic traces, and sensor-message summaries. A metadata file is organised into the following main sections:

- `event_uid`: anonymised event identifier
- `event_name`: event/action name, such as `stop`, `slow down`, or `lane change`
- `window`: event timing information, including the pre-event and post-event window
- `csv`: annotation and explanation fields derived from the curated dataset table
- `clicker`: event-tagging information when available
- `assets`: relative paths to the available event files
- `sensor_message_counts`: message counts for included sensor topics

### Metadata: `window`

The `window` section describes the event time span:

- `before_event_s`: seconds of context before the tagged event
- `after_event_s`: seconds of context after the tagged event
- `elapsed_time_s`: event time in the original drive session
- `start_elapsed_s` and `end_elapsed_s`: start and end of the extracted event window
- `event_timestamp_ns`, `start_timestamp_ns`, and `end_timestamp_ns`: nanosecond timestamps for synchronising the event with sensor data

### Metadata: `csv`

The `csv` section contains the main curated event annotations and explanation fields:

- `driver_action_annotation`
- `in_vehicle_explanation`
- `post_explanation`
- `word_count_iv`
- `word_count_post`
- `sa_L1_iv`, `sa_L2_iv`, `sa_L3_iv`
- `sa_L1_post`, `sa_L2_post`, `sa_L3_post`
- `sa_labels_in_vehicle`
- `sa_labels_post`
- `context`
- `context_high_level`
- `context_fine_grained`
- `clip_duration_sec`
- `fps`
- `speed`
- `acceleration_x`
- `statistics`
- `split`
- `driver_action_clean`
- `primary_text`
- `elicitation_type`

`in_vehicle_explanation` is the explanation collected during the drive, when the participant explained their action in the vehicle. `post_explanation` is the interview explanation collected after the drive during the video-cued post-drive interview. Some events have only an in-vehicle explanation, some have only a post-drive explanation, and some may contain both.

Situational Awareness labels follow three levels:

- **L1 Perception**: information the driver noticed
- **L2 Comprehension**: the driving relevance or interpretation of that information
- **L3 Projection**: anticipation of a future state, outcome, or risk

The fields beginning with `sa_` refer to Situational Awareness annotations. The suffix indicates whether the label applies to the in-vehicle explanation (`iv`) or the post-drive interview explanation (`post`):

- `sa_L1_iv`, `sa_L2_iv`, `sa_L3_iv`: binary indicators for whether L1, L2, or L3 SA appears in the in-vehicle explanation
- `sa_L1_post`, `sa_L2_post`, `sa_L3_post`: binary indicators for whether L1, L2, or L3 SA appears in the post-drive explanation
- `sa_labels_in_vehicle`: span-level SA labels over the in-vehicle explanation text
- `sa_labels_post`: span-level SA labels over the post-drive explanation text

The span-level SA fields identify the exact character spans in the explanation text that correspond to each SA level. For example, a span labelled `L1_SA` marks words describing something the driver perceived, while `L2_SA` marks interpretation or relevance, and `L3_SA` marks anticipation of what may happen next.

Scenario-context labels describe the driving situation at the event level. The paper reports six high-level context groups and 32 fine-grained scenario categories.

The kinematic fields provide event-level motion traces and summaries:

- `speed`: sampled vehicle speed trace across the event window
- `acceleration_x`: sampled longitudinal acceleration trace across the event window
- `statistics`: summary values such as minimum, maximum, and mean speed or acceleration

The `split` field identifies the benchmark partition for the event, such as `train`, `validation`, or `test`. The `primary_text` field provides the main explanation text used for modelling, typically the in-vehicle explanation when available and otherwise the post-drive explanation. The `elicitation_type` field records how the event explanation was elicited or triggered during data collection.

### Metadata: `clicker`

The `clicker` section contains event-tagging information recorded during the drive:

- `elapsed_time_s`: tagged event time within the drive
- `event`: event/action name recorded at collection time
- `event_type`: event category recorded by the collection interface
- `explanation_length`: whether the in-vehicle explanation was marked as short or sufficiently informative
- `event_id`: anonymised event identifier in the released metadata

### Metadata: `assets`

The `assets` section lists the relative paths to the files associated with the event. These paths connect the metadata JSON to the available camera clips and sensor bag folder, for example:

```text
front_camera/abcd-0001_front_camera.mp4
front_left_camera/abcd-0001_front_left_camera.mp4
front_right_camera/abcd-0001_front_right_camera.mp4
rear_camera/abcd-0001_rear_camera.mp4
sensor_bags/abcd-0001_sensors
```

### Metadata: `sensor_message_counts`

The `sensor_message_counts` section reports how many ROS 2 messages are included for each released sensor topic in the event window. These counts help users check which sensor streams are present for an event and how much data each stream contains.

## Sensor Bags

The `sensor_bags/` folder contains event-level ROS 2 bag folders for non-video sensor streams:

```text
sensor_bags/abcd-0001_sensors/
```

A typical sensor folder contains:

```text
abcd-0001_sensors_0.db3
metadata.yaml
```

The `.db3` file stores ROS 2 sensor messages, and `metadata.yaml` describes the bag contents. The released sensor bags may include:

- LiDAR point clouds
- GNSS/GPS position
- IMU measurements
- odometry/localisation state
- transform frames (`/tf` and `/tf_static`)

These sensor files are intended to be used together with the corresponding anonymised camera clips and metadata JSON for the same event.

## Data Collection

NARRATE was collected on public roads in Brisbane CBD, Queensland, Australia. Participants drove a predefined route in a right-hand-drive vehicle in a left-hand-traffic Australian road environment.

Each session included:

- real-world driving on public roads
- in-vehicle explanation elicitation when safe and appropriate
- event tagging during the drive
- post-drive video-cued interview using synchronised multi-view event clips

The dataset captures both immediate in-vehicle explanations and reflective post-drive explanations. This supports research into how experienced drivers perceive, interpret, and anticipate real traffic situations.

## Annotations

NARRATE provides multiple annotation layers:

- driver-action labels
- scenario-context labels
- in-vehicle free-text explanations
- post-drive free-text explanations
- span-level Situational Awareness annotations over driver explanations
- event-level timing and asset metadata

The dataset is intended for tasks such as:

- Situational Awareness classification
- scenario-context classification
- driver-action classification
- multimodal driving-event understanding
- natural-language explanation generation for automated driving

## Citation

If you use NARRATE in your research, please cite:

> Yousefi Zadeh, Ashkan; Zhu, Zishuo; Li, Xiaomeng; Rakotonirainy, Andry; Glaser, Sebastien; Schroeter, Ronald; ARC Training Centre for Automated Vehicles in Rural and Remote Regions (AVR3); (2026): NARRATE: A Multimodal Real-World Australian Driving Dataset for Human-Centred Explanations in Automated Driving (Version 1). Queensland University of Technology. (Dataset) https://doi.org/10.25912/RDF_1786669427992

```bibtex
@misc{yousefizadeh2026narrate,
  author    = {Yousefi Zadeh, Ashkan and Zhu, Zishuo and Li, Xiaomeng and
               Rakotonirainy, Andry and Glaser, Sebastien and Schroeter, Ronald and
               {ARC Training Centre for Automated Vehicles in Rural and Remote Regions (AVR3)}},
  title     = {{NARRATE}: A Multimodal Real-World Australian Driving Dataset for
               Human-Centred Explanations in Automated Driving (Version 1)},
  year      = {2026},
  publisher = {Queensland University of Technology},
  type      = {Dataset},
  doi       = {10.25912/RDF_1786669427992},
  url       = {https://doi.org/10.25912/RDF_1786669427992}
}
```

## Licence and Conditions of Use

This dataset is released under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) licence.

Dataset access is mediated through QUT Research Data Finder. Users must also follow the ethics, privacy, and data-use conditions specified as part of the official access process.

This GitHub repository does not redistribute the dataset files.

## Contact

For questions regarding the dataset, please contact [ashkan.zadeh@qut.edu.au](mailto:ashkan.zadeh@qut.edu.au).

## Acknowledgements

This dataset was developed at Queensland University of Technology through the ARC Training Centre for Automated Vehicles in Rural and Remote Regions (AVR3).

This research was supported by the Australian Research Council Discovery Project (DP220102598).
