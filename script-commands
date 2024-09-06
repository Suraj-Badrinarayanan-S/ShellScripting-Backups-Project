#!/bin/bash

<< readme
This is a script for backup with a 3 day rotation

Usage:

./backup.sh <source-path> <backup-path>
readme

function display_usage {
        echo "Usage: ./backup.sh <source-path> <backup-path>"
}

if [ $# -eq 0 ]; then
        display_usage
fi

source_dir=$1
backup_dir=$2
timestamp=$(date '+%Y-%m-%d-%H-%M-%S')
function create_backup {
        zip -r "${backup_dir}/backup_${timestamp}.zip" "${source_dir}" > /dev/null

        if [ $? -eq 0 ]; then
                echo "backup generated successfully for ${timestamp}"
        fi
}


function perform_rotation {
        backups=($(ls -t "${backup_dir}/backup_"*.zip ))

        if [ "${#backups[@]}" -gt 3 ]; then
                echo "Performing rotation for 3 days"

                backups_to_remove=("${backups[@]:3}")

                for backup in "${backups_to_remove[@]}";
                do
                        rm -f ${backup}
                done
        fi
}

create_backup
perform_rotation
