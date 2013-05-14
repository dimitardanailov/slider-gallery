<?php

/**
 *
 *
 * Copyright (c) 2010 158, Ltd.
 * All Rights Reserved.
 *
 * Redistribution and use in source and binary forms, with or without
 * modification are not permitted.
 *
 * Neither the name of 158, Ltd. or the names of contributors
 * may be used to endorse or promote products derived from this software
 * without specific prior written permission.
 *
 * This software is provided "AS IS," without a warranty of any kind. ALL
 * EXPRESS OR IMPLIED CONDITIONS, REPRESENTATIONS AND WARRANTIES, INCLUDING
 * ANY IMPLIED WARRANTY OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
 * PURPOSE OR NON-INFRINGEMENT, ARE HEREBY EXCLUDED. 158 AND ITS LICENSORS
 * SHALL NOT BE LIABLE FOR ANY DAMAGES SUFFERED BY LICENSEE AS A RESULT OF
 * USING, MODIFYING OR DISTRIBUTING THE SOFTWARE OR ITS DERIVATIVES. IN NO
 * EVENT WILL 158 OR ITS LICENSORS BE LIABLE FOR ANY LOST REVENUE, PROFIT
 * OR DATA, OR FOR DIRECT, INDIRECT, SPECIAL, CONSEQUENTIAL, INCIDENTAL OR
 * PUNITIVE DAMAGES, HOWEVER CAUSED AND REGARDLESS OF THE THEORY OF
 * LIABILITY, ARISING OUT OF THE USE OF OR INABILITY TO USE SOFTWARE, EVEN
 * IF 158 HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.
 *
 * Any violation of the copyright rules above will be punished by the lay.
 */


class DirectoryTool {
    public $filepath;
    public function __construct($filepath) {
        $this->filepath = $filepath;
    }

    /**
     * <p>Deletes all the files from the given folder And Delete Folder</p>
     */
    function deleteAllFilesAndFolder() {
        foreach (glob($this->filepath."/*") as $filename) {
            unlink($filename);
        }

        if(file_exists($this->filepath))
        {
            rmdir($this->filepath);
        }
    }

    /**
     * <p>Deletes all the files from the given folder</p>
     */
    function deleteAllFiles() {
        foreach (glob($this->filepath."/*") as $filename) {
            unlink($filename);
        }
    }

    /**
    * <p>Deletes all the files and subfolders from the given folder</p>
    */
    function deleteAllFilesAndSubfolders($target=NULL)
    {
        if($target==NULL)
        {
            $target = $this->filepath;
        }

        if (is_dir($target))
        {

            $objects = scandir($target);

            foreach ($objects as $object)
            {
                if ($object != "." && $object != "..")
                {
                    if (filetype($target."/".$object) == "dir")
                    {
                        $this->deleteAllFilesAndSubfolders($target."/".$object);
                    }
                    else
                    {
                        unlink($target."/".$object);
                    }
                }
            }
            reset($objects);
            rmdir($target);
        }
    }

    /**
     * <p>Lists all files in a folder</p>
     * @return array an array with all the files in the folder
     */
    function listFiles() {
        $array_filenames = array();

        foreach (glob($this->filepath."/*") as $filename) {
            $array_filenames[] = $filename;
        }

        return $array_filenames;
    }

    /**
     * <p>Filters files by extensions</p>
     * @param array $extations Array with extensions for filtering
     * @return array the filtered filelist
     */
    function listFilesByExtension($extensions) {

        $array_filenames = array();

        foreach ($extensions as $key=>$value) {
            foreach (glob($this->filepath."/*.".$value) as $filename) {
                $array_filenames[] = $filename;
            }

        }
        return $array_filenames;
    }
}
?>
