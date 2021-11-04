.. _DownloadCandidateRequirements:

UC: Download Candidate's Requirements
=================================================================================================================================

``DownloadCandidateRequirements``

Triggers:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User wants to download Candidate's Requirements to the Recruitment Platform

Pre-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Description:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. uml::

    @startuml

        actor "Recruiter" as Recruiter
        participant "UI" as UI
        participant "Database" as Database

        Recruiter  -> UI: Click button to download Candidate's Requirements
        UI -> Recruiter: Show option to select the file for download
        Recruiter -> UI: Select the file and click Download

        UI -> Database: Download file to Database
        
        alt Download is Successful
            Database -> UI: //Download Successful//
            UI -> Recruiter: //Download Successful//
        else
            Database -> UI: //Download Unsuccessful//
            UI -> Recruiter: //Download Unsuccessful//

            note over Database, UI
                Database may have many types of errors. 
                The error cases we support still needs to be determined
            end note
        end

    @enduml

Post-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    Candidate's Requirements are downloaded successfully.

Exceptions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Notes and Issues:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

References to High-Level Requirements:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    - :ref:`StoreApplicationDocuments`
    - :ref:`StorePreOnboardingRequirements`
    - :ref:`UserProfileShowsRequirementsAlreadySubmitted`
