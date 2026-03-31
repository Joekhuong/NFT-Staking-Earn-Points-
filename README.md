# NFT-Staking-Earn-Points-
NFT Staking (Earn Points)
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

contract NFTStaking {
    IERC721 public nft;
    mapping(address => uint256) public points;

    constructor(address _nft) {
        nft = IERC721(_nft);
    }

    function stake(uint256 tokenId) public {
        nft.transferFrom(msg.sender, address(this), tokenId);
        points[msg.sender] += 1;
    }
}
