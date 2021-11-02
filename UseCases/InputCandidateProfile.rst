.. _InputCandidateProfile:

UC: Input Candidate Profile
=================================================================================================================================

``InputCandidateProfile``

Triggers:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User wants to enter information about a candidate

Pre-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Description:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. uml::

    @startuml

        actor "Recruiter" as Recruiter
        participant "UI" as UI
        participant "Parser" as Parser
        participant "Database" as Database

        alt Manually enter Data to Website
            Recruiter  -> UI: Enter Data to website

            note over UI
                Data is displayed in the website as you type
            end note

        else Upload Resume and use the Automatic Parser
            Recruiter  -> UI: Click button to upload Resume
            UI -> Recruiter: Show option to select the file for upload
            Recruiter -> UI: Select the resume and click Upload
            UI -> Parser: Resume will be parsed
            Parser -> UI: Show the parsed fields

            note over Parser, UI
                Not all fields can be shown on the UI. 
                See Notes section for more details.
            end note
        end
        

        Recruiter -> UI: Click Save
        UI -> UI: Perform Data Validation

        alt Input data does not follow requirements
            UI -> Recruiter: Notify User of errors so that he/she can correct them.
        end

        UI -> Database: Store entry to Database

    @enduml

Post-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User profile is saved to the :term:`Database`.

Exceptions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Notes and Issues:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    1. Not all fields can be parsed properly since there is no universal format for a Resume.
       For a list of fields of fields that we can auto-populate, please see :ref:`AutoPopulateUsingParser`

References to High-Level Requirements:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    - :ref:`FormatForDates`
    - :ref:`FormatForEmail`
    - :ref:`FormatForTelephoneNumbers`
    - :ref:`UserCanInputCandidateProfile`
    - :ref:`AutoPopulateUsingParser`
